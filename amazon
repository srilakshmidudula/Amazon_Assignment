package appium;

import java.net.MalformedURLException;
import java.net.URL;
import java.time.Duration;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.interactions.touch.TouchActions;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.Test;

import io.appium.java_client.TouchAction;
import io.appium.java_client.android.AndroidDriver;
import io.appium.java_client.touch.WaitOptions;
import io.appium.java_client.touch.offset.PointOption;

public class amazon {
	AndroidDriver<WebElement> driver=null;
	@Test
	public void test() throws MalformedURLException, InterruptedException {
		
		
		DesiredCapabilities capability=new DesiredCapabilities();
		//capabilities to launch amazon native application
		capability.setCapability("deviceName", "Redmi Note 5 Pro");
		capability.setCapability("platformVersion", "8.1.0");
		capability.setCapability("PlatformName", "Android");
		capability.setCapability("appPackage", "com.amazon.mShop.android.shopping");
		capability.setCapability("appActivity", "com.amazon.mShop.splashscreen.StartupActivity");
		driver=new AndroidDriver<WebElement>(new URL("http://192.168.43.147:4723/wd/hub"), capability);
	    driver.manage().timeouts().implicitlyWait(40, TimeUnit.SECONDS);
	   // if(driver.findElementById("com.amazon.mShop.android.shopping:id/skip_sign_in_button").isDisplayed())
	   // 	driver.findElementById("com.amazon.mShop.android.shopping:id/skip_sign_in_button").click();
	    driver.findElementById("com.amazon.mShop.android.shopping:id/action_bar_burger_icon").click();
	    Assert.assertTrue(driver.findElementByXPath("//*[contains(@text,'Hello')]").isDisplayed(), "hamburgur menu is not opened");
	    driver.findElement(By.xpath("//*[contains(@text,'Settings')]")).click();
	    driver.findElement(By.xpath("//*[@resource-id='com.amazon.mShop.android.shopping:id/anp_drawer_item'][1]")).click();
	    //country options are loading slowly sometimes
	    Thread.sleep(10000);
	    driver.findElement(By.xpath("//*[contains(@text,'Country/Region:')][1]")).click();
	    driver.findElement(By.xpath("//*[contains(@text,'Australia')]")).click();
	    driver.findElement(By.xpath("//*[contains(@text,'Done')][1]")).click();
	    driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
	       
	    WebElement search=driver.findElementById("com.amazon.mShop.android.shopping:id/rs_search_src_text");
	    search.click();
	    search.sendKeys("dress");
	    System.out.println(driver.manage().window().getSize());
	    //we can't able to take id for keyboard in android, so using touchactions to click on search.
	    TouchAction action=new TouchAction(driver);
	    action.tap(new PointOption().withCoordinates(1075, 2020)).perform();
	    
	    
}
	
	  @AfterTest public void after() throws InterruptedException {
		  driver.removeApp("io.appium.settings");
		  driver.removeApp("io.appium.unlock");
		  driver.quit(); 
		  }
	 
}
