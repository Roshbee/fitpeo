# fitpeo
package newpractice;

import java.util.Iterator;
import java.util.List;
import java.util.Set;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Filpkart {

	public static void main(String[] args) throws InterruptedException {
		System.setProperty("webdriver.chrome.driver", "D:\\workspace\\SELENIUM\\driver1\\chromedriver.exe");
		WebDriver driver = new ChromeDriver();
		//Maximized the window
		driver.manage().window().maximize();
		//opened the url
		driver.get("https://www.flipkart.com");
		//removed the popup from screen
		driver.findElement(By.xpath("//button[@class='_2KpZ6l _2doB4z']")).click();
		//searched the product
		driver.findElement(By.name("q")).sendKeys("ipad");
		driver.findElement(By.xpath("//button[@class='L0Z3Pu']")).click();
		Thread.sleep(3000);
		//clicked on the one of the product 
		WebElement l = driver
				.findElement(By.xpath("//*[@id=\"container\"]/div/div[3]/div[1]/div[2]/div[2]/div/div/div/a"));
		JavascriptExecutor j = (JavascriptExecutor) driver;
		j.executeScript("arguments[0].click();", l);
		Thread.sleep(3000);
//new window opened so switched to that window
		String parentwindowString = driver.getWindowHandle();
		Set<String> allhandleSet = driver.getWindowHandles();
		Iterator<String> iterator = allhandleSet.iterator();
		while (iterator.hasNext()) {
			String childwindowString = iterator.next();
			if (!parentwindowString.equalsIgnoreCase(childwindowString)) {
				driver.switchTo().window(childwindowString);

			}
		}
		//checkout the product
		driver.findElement(By.xpath("//button[@class='_2KpZ6l _2U9uOA ihZ75k _3AWRsL']")).click();
		Thread.sleep(3000);
		//entered the random credentials
		driver.findElement(By.xpath("//input[@class='_2IX_2- _17N0em']")).sendKeys("Abcdefgh@gmail.com");

	}

}
