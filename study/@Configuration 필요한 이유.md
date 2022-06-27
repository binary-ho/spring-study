# @Configuration 
@Configuration 애노테이션을 사용하면 해당 파일이 설정 파일이고, 여기에 Bean을 등록할 거라고 알려줄 수가 있다. <br>
그냥  AnnotationConfigApplicationContext() 안에 적어줘도 되는거 아닌가? 아니다.

```java
package Test.sample;

import Test.sample.calculate.Calculate;
import Test.sample.calculate.Calculator;
import Test.sample.calculate.Minus;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public Calculate calculate(){
        System.out.println("AppConfig.calculate");
        return new Minus();
    }

    @Bean
    public Calculator calculator(){
        System.out.println("AppConfig.calculator");
        return new Calculator(calculate());
    }

}
```
위와 같은 코드에서 테스트를 진행한다면, 원래는 clculator안에 calculate를 실행하는 부분이 있으므로, 
Appconfig.calculate, Appconfig.calculator, Appconfig.calculate 3개가 출력되어야 한다.     <br>

**그런데 @Configuration을 이용해서 명시적으로 설정파일임을 알려주면 알아서 Bean들을 싱글톤으로 유지시켜 주기 때문에, 
Appconfig.calculate, Appconfig.calculator 두개만 찍히게 된다.**
