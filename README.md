**Resumo das Anotações do Spring Boot em Português:**

### Anotações Gerais do Spring Boot:

1. **@SpringBootApplication:**
   - Utilizada para marcar a classe principal de uma aplicação Spring Boot.
   - Encapsula outras anotações como @SpringBootConfiguration, @EnableAutoConfiguration e @ComponentScan.

   *Exemplo:*
   ```java
   @SpringBootApplication
   public class MinhaAplicacao {
       public static void main(String[] args) {
           SpringApplication.run(MinhaAplicacao.class, args);
       }
   }
   ```

2. **@SpringBootConfiguration:**
   - Anotação de nível de classe indicando que a classe fornece configuração para uma aplicação Spring Boot.
   - Pode ser usada como alternativa à anotação padrão @Configuration do Spring.

   *Exemplo:*
   ```java
   @SpringBootConfiguration
   public class MinhaConfiguracao {
       // Métodos de configuração aqui
   }
   ```

3. **@EnableAutoConfiguration:**
   - Autoconfigura beans presentes no classpath, simplificando o trabalho do desenvolvedor ao assumir as configurações necessárias para executar a aplicação.

   *Exemplo:*
   ```java
   @Configuration
   @EnableAutoConfiguration
   public class MinhaConfiguracao {
       // Métodos de configuração aqui
   }
   ```

4. **@ComponentScan:**
   - Indica a quais pacotes o Spring deve escanear em busca de componentes, como controllers e services.
   - Geralmente usada em conjunto com @Configuration para especificar o pacote a ser escaneado.

   *Exemplo:*
   ```java
   @Configuration
   @ComponentScan(basePackages = "com.exemplo.pacote")
   public class MinhaConfiguracao {
       // Métodos de configuração aqui
   }
   ```

5. **Condições de Autoconfiguração:**
   - Diversas anotações como @ConditionalOnClass, @ConditionalOnBean, @ConditionalOnProperty, etc., são usadas para configurar automaticamente componentes com base em condições específicas.

### Anotações para Manipulação de Requisições e Controllers:

1. **@Controller:**
   - Indica que a classe é um controlador Spring MVC, manipulando requisições HTTP.
   
   *Exemplo:*
   ```java
   @Controller
   public class MeuController {
       // Métodos manipuladores aqui
   }
   ```

2. **@RestController:**
   - Utilizada para criar controladores que lidam com APIs RESTful, combinando @Controller e @ResponseBody.

   *Exemplo:*
   ```java
   @RestController
   public class MeuRestController {
       // Métodos manipuladores de APIs RESTful aqui
   }
   ```

3. **@RequestMapping:**
   - Mapeia requisições HTTP para métodos em um controlador.
   
   *Exemplo:*
   ```java
   @Controller
   public class MeuController {
       @RequestMapping(value = "/exemplo", method = RequestMethod.GET)
       public String exemplo() {
           // Lógica aqui
       }
   }
   ```

4. **@RequestParam:**
   - Obtém parâmetros da URI em requisições HTTP. Usado para ler dados de formulários.

   *Exemplo:*
   ```java
   @GetMapping("/autores")
   public String obterAutores(@RequestParam(name = "nomeAutor") String nome) {
       // Lógica aqui
   }
   ```

5. **@PathVariable:**
   - Extrai dados do caminho da URI para métodos em um controlador.
   
   *Exemplo:*
   ```java
   @GetMapping("/autor/{nomeAutor}")
   public String obterNomeAutor(@PathVariable(name = "nomeAutor") String nome) {
       // Lógica aqui
   }
   ```

6. **@RequestBody:**
   - Converte o corpo de requisições HTTP em objetos de domínio.

   *Exemplo:*
   ```java
   @PostMapping("/autor")
   public void adicionarAutor(@RequestBody Autor autor) {
       // Lógica aqui
   }
   ```

7. **@ResponseBody:**
   - Converte objetos de domínio em respostas HTTP, geralmente no formato JSON.

   *Exemplo:*
   ```java
   @GetMapping("/autor")
   public @ResponseBody Autor obterAutor() {
       Autor autor = new Autor();
       // Lógica para preencher autor
       return autor;
   }
   ```

8. **@ModelAttribute:**
   - Refere-se a objetos modelo no Spring MVC, podendo ser usado em métodos ou argumentos de métodos.

   *Exemplo:*
   ```java
   @ModelAttribute("autor")
   public Autor obterAutor() {
       // Lógica para criar e retornar um autor
   }
   ```
