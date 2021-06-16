    public class FaceTeste {
    WebDriver driver;

    @Before
    public void antes(){
      // Configura Selenium
        System.setProperty("webdriver.chrome.driver","C:\\WebDriver\\chromedriver.exe");
        driver = new ChromeDriver();
        driver.manage().window().maximize();

        driver.get("https://pt-br.facebook.com/r.php");
    }

    @Test
    public void facebookTesteLogin() throws InterruptedException {

        // Preenhe Campos de cadastro
        driver.findElement(By.name("firstname")).sendKeys("Jeanne");
        driver.findElement(By.name("lastname")).sendKeys("Barbosa");
        driver.findElement(By.name("reg_email__")).sendKeys("jeannebarbosa@gmail.com");
        driver.findElement(By.name("reg_email_confirmation__")).sendKeys("jeannebarbosa@gmail.com");
        driver.findElement(By.name("reg_passwd__")).sendKeys("123asd");

        // Preenche os select de data
        WebElement comboDia = driver.findElement(By.id("day"));
        Select select = new Select(comboDia);
        select.selectByVisibleText("26");

        WebElement comboMes = driver.findElement(By.id("month"));
        select = new Select(comboMes);
        select.selectByVisibleText("Mar");

        WebElement comboAno = driver.findElement(By.id("year"));
        select = new Select(comboAno);
        select.selectByVisibleText("1985");

        // Escolha do gênero
        driver.findElement(By.xpath("//input[@value='1']")).click();

        // Clica no botão Entrar
        driver.findElement(By.name("websubmit")).click();
    }
        //  Fecha a página após ser vizualizada
        // @After
        // public void depois(){
        //    driver.quit();

    }
