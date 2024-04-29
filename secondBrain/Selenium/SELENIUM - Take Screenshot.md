

----
Creation date: 2022-04-30 22:13
Modification date: Saturday 30th April 2022 22:13:30

----

Tags: [[selenium]]

> Wisdom has never made a bigot, but learning has.
> — <cite>Josh Billings</cite>

We can use it in annotation @AfterMethod, which means it will take a screenshot after each test.

```java
@AfterMethod 
public void recordFailed(ITestResult result ){ 
	if(ITestResult._FAILURE_ == result.getStatus()){ 
		TakesScreenshot camera = (TakesScreenshot) driver; 
		File screenshot = camera.getScreenshotAs(OutputType._FILE_); 
		try{ 
			Files._move_(screenshot, new File("resources/screenshot/" + result.getName() + ".png")); 
		}catch (IOException e){ 
			e.printStackTrace(); 
		} 
	} 
}
```


1.  Sử dụng "TakesScreenshot" Selenium class để chụp màn hình trên trình duyệt
2.  Sử dụng phương thức "getScreenShotAs()" để chụp màn hình
3.  Để sử dụng lớp "TakesScreenshot" chụp màn hình, chúng ta cần cast nó vào đối tượng WebDriver.