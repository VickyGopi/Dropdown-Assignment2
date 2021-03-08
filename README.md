package week4.day1;

import java.awt.Desktop.Action;
import java.io.File;
import java.io.IOException;
import java.util.concurrent.TimeUnit;

import org.apache.commons.io.FileUtils;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;

import io.github.bonigarcia.wdm.WebDriverManager;

public class Assignment2 {

	public static void main(String[] args) throws IOException {
		WebDriverManager.chromedriver().setup();
		ChromeDriver driver = new ChromeDriver();
		driver.get("http://leafground.com/pages/Dropdown.html");
		driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
		driver.manage().window().maximize();
		WebElement source=driver.findElement(By.xpath("(//select)[6]//following::option[text()='Appium']"));
		WebElement target=driver.findElement(By.xpath("(//select)[6]//following::option[text()='Loadrunner']"));
		Actions actionsObj=new Actions(driver);
		actionsObj.keyDown(Keys.CONTROL).click(source).click(target).keyUp(Keys.CONTROL).perform();
		File source1 = driver.getScreenshotAs(OutputType.FILE);
		File target1 = new File ("./snaps/Dropdown.png");
		FileUtils.copyFile(source1, target1);
	}
}
