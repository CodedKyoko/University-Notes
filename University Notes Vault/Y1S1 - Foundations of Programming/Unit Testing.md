- A unit test checks a small piece of code in isolation, such as one method.
- Automated tests can be rerun after changes and reveal any regressions.
- A passing test provides evidence for the cases checked; not proof that every input works.

>[!Arrange]
>Choose inputs and expected result

>[!Act]
>Call the method being tested

>[!Assert]
>Compare the actual result with the expectation
>A failed assertion marks the test as failed and helps indentify a mismatch.

>[!Example]
>```cs
>using GradeApp;  
>using Microsoft.VisualStudio.TestTools.UnitTesting;  
>
>[TestClass]  
>public class GradeToolsTests  {  
>	[TestMethod]  
>	public void GetResult_Score49_ReturnsFail()  {  
>		int score = 49;  
>		string expected = "Fail";  
>		string actual = GradeTools.GetResult(score);  
>		Assert.AreEqual(expected, actual);  
>	}  
>}
>```

