---
title: 使用填充碼將應用程式與其他組件隔離，方便進行單元測試 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 14
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2ab2925024fdf9e4f0b4e93db34b375b89933a48
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155939"
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>使用填充碼將應用程式與其他組件隔離，方便進行單元測試
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

填充碼類型**是 Microsoft Fakes Framework 兩項技術的其中一個，讓您輕鬆地隔離待測元件與環境。 填充碼會將指向特定方法的呼叫轉向至您撰寫來做為測試一部分的程式碼。 有許多方法會取決於外部條件傳回不同的結果，不過填充碼會受您的測試所控制，並且可在每個呼叫中傳回一致的結果。 這可讓您更容易撰寫測試。  
  
 使用填充碼來隔離您的程式碼以及不屬於方案的組件。 若要互相隔離方案的元件，我們建議您使用虛設常式。  
  
 如需概觀和快速入門指南，請參閱[使用 Microsoft Fakes 在測試期間隔離程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)。  
  
 **需求**  
  
- Visual Studio 企業版  
  
  請參閱 [Video (1h16): Testing Un-testable Code with Fakes in Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837) (影片 (1 小時 16 分鐘)：在 Visual Studio 2012 中使用 Fakes 測試不可測試的程式碼)
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> 範例：Y2K Bug  
 考慮在 2000 年 1 月 1 日擲回例外狀況的方法：  
  
```csharp  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }
}  
  
```  
  
 測試這個方法會特別有問題，因為此程式依賴 `DateTime.Now`，這是一種取決於電腦時鐘、環境相依且不具決定性的方法。 此外，`DateTime.Now` 是靜態屬性，因此不能在這裡使用虛設常式類型。 這個問題是單元測試中隔離問題的根源：直接呼叫資料庫應用程式開發介面、與 Web 服務進行通訊等的程式，一直難以進行單元測試，因為其邏輯取決於環境。  
  
 這是應該使用填充碼類型的情況。 填充碼類型提供一個機制，將所有 .NET 方法繞道至使用者定義的委派。 填充碼類型是由 Fakes 產生器以程式碼產生的，並使用我們稱為填充碼類型的委派來指定新的方法實作。  
  
 下列測試顯示如何使用填充碼類型 `ShimDateTime`，提供 DateTime.Now 的自訂實作：  
  
```csharp  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> 如何使用填充碼  
  
###  <a name="AddFakes"></a> 新增 Fakes 組件  
  
1.  在方案總管中，展開單元測試專案的 [參考]。  
  
    -   如果您在 Visual Basic 中工作，必須先選取方案總管工具列中的 [顯示所有檔案]，才能看見 [參考] 清單。  
  
2.  選取包含您要用於建立填充碼之類別定義的組件。 例如，如果您要填充日期時間，請選取 System.dll。  
  
3.  在捷徑功能表上，選擇 [新增 Fakes 組件]。  
  
###  <a name="ShimsContext"></a> 使用 ShimsContext  
 在單元測試架構中使用填充碼類型時，您必須包裝 `ShimsContext` 中的測試程式碼，藉此控制填充碼的存留期。 如果我們不要求這樣做，您的填充碼可能會持續存在，直到 AppDomain 關閉為止。 建立 `ShimsContext` 的最簡單方式為使用靜態 `Create()` 方法，如下列程式碼所示：  
  
```csharp  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 請務必適當處置每個填充碼內容。 根據經驗法則，請一律呼叫 `using` 陳述式內的 `ShimsContext.Create`，以確保適當清除已註冊的填充碼。 例如，您可能會註冊測試方法的填充碼，將 `DateTime.Now` 方法取代成永遠都會傳回 2000 年 1 月 1 日的委派。 如果您忘記清除在測試方法中註冊的填充碼，則測試回合的其餘部分一定會傳回 2000 年 1 月 1 日做為 DateTime.Now 的值。 這可能會讓人感到意外和混淆。  
  
###  <a name="WriteShims"></a> 撰寫含填充碼的測試  
 在您的測試程式碼中，請插入您要假造之方法的「繞道」。 例如：  
  
```csharp  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet =   
                () =>  
                { return new DateTime(fixedYear, 1, 1); };  
  
                // Instantiate the component under test:  
                var componentUnderTest = new MyComponent();  
  
              // Act:  
                int year = componentUnderTest.GetTheCurrentYear();  
  
              // Assert:   
                // This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year);  
            }  
        }  
}  
  
```  
  
```vb  
<TestClass()> _  
Public Class TestClass1  
    <TestMethod()> _  
    Public Sub TestCurrentYear()  
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
            Dim fixedYear As Integer = 2000  
            ' Arrange:  
            ' Detour DateTime.Now to return a fixed date:  
            System.Fakes.ShimDateTime.NowGet = _  
                Function() As DateTime  
                    Return New DateTime(fixedYear, 1, 1)  
                End Function  
  
            ' Instantiate the component under test:  
            Dim componentUnderTest = New MyComponent()  
            ' Act:  
            Dim year As Integer = componentUnderTest.GetTheCurrentYear  
            ' Assert:   
            ' This will always be true if the component is working:  
            Assert.AreEqual(fixedYear, year)  
        End Using  
    End Sub  
End Class  
```  
  
 填充碼類別名稱是在原始類型名稱前面加上 `Fakes.Shim` 而構成。  
  
 填充碼藉由將「繞道」插入至受測應用程式的程式碼中來運作。 只要原始方法的呼叫發生，Fakes 系統就會執行繞道，因此呼叫的是您的填充程式碼，而不是呼叫實際的方法。  
  
 請注意繞道會在執行階段建立和刪除。 一定要在 `ShimsContext` 的生命週期內建立繞道。 在處置繞道的時候，會移除您在繞道作用時建立的任何填充碼。 最好的做法是在 `using` 陳述式內進行。  
  
 您可能會看到建置錯誤，指出 Fakes 命名空間不存在。 當有其他的編譯錯誤時，有時候會出現這個錯誤。 請修正其他錯誤，該錯誤也將消失。  
  
##  <a name="BKMK_Shim_basics"></a> 不同方法類型的填充碼  
 填充碼類型可讓您用自己的委派取代所有 .NET 方法，包含靜態方法或非虛擬方法。  
  
###  <a name="BKMK_Static_methods"></a> 靜態方法  
 要附加填充碼到靜態方法的屬性放置於填充碼類型中。 每個屬性都只有一個 Setter 可以用來附加委派至目標方法。 例如，給定一個具有 `MyMethod` 靜態方法的 `MyClass` 類別：  
  
```csharp  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 我們可在始終傳回 5 的 `MyMethod` 附加填充碼：  
  
```csharp  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> 執行個體方法 (針對所有執行個體)  
 與靜態方法類似，執行個體方法可針對所有執行個體填充。 附加這些填充碼的屬性放置在名為 AllInstances 的巢狀類型以避免混淆。 例如，給定一個具有 `MyMethod` 執行個體方法的 `MyClass` 類別：  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 不論這個執行個體為何，您可以在始終傳回 5 的 `MyMethod` 附加填充碼：  
  
```csharp  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 ShimMyClass 之產生的類型結構看起來像下列程式碼：  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 請注意在這種情況下，Fakes 會將執行階段執行個體做為委派的第一個引數傳遞。  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> 執行個體方法 (針對某一個執行階段執行個體)  
 根據呼叫的接收器，執行個體方法可以由不同的委派來填充。 這可讓相同的執行個體方法對於每種類型的執行個體具有不同行為。 設定這些填充碼的屬性是此填充碼類型本身的執行個體方法。 每一個具現化的填充碼類型也與已填充類型之未經處理的執行個體相關聯。  
  
 例如，給定一個具有 `MyMethod` 執行個體方法的 `MyClass` 類別：  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 我們可以設定 MyMethod 的兩種填充碼類型，使得第一個一律傳回 5，而第二個一律傳回 10：  
  
```csharp  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 ShimMyClass 之產生的類型結構看起來像下列程式碼：  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 實際已填充類型的執行個體可以透過執行個體屬性來存取：  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 填充碼類型也會對已填充類型做隱含轉換，因此您通常可以直接使用填充碼類型：  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> 建構函式  
 也可以填充建構函式，用來將填充碼類型附加到未來的物件。 會將每個建構函式公開為此填充碼類型中的靜態方法建構函式。 例如，給定一個具有接受整數之建構函式的 `MyClass` 類別：  
  
```csharp  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 我們設定此建構函式的填充碼類型，使得不論在此建構函式中的值為多少，當值 Getter 被叫用時，每個未來的執行個體都會傳回 -5：  
  
```csharp  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 請注意每個填充碼類型都會公開兩個建構函式。 在需要新執行個體時，應使用預設建構函式；而將已填充的執行個體當做引數的建構函式，只應該用在建構函式填充碼：  
  
```csharp  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 ShimMyClass 之產生的類型結構類似下列程式碼：  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a> 基底成員  
 藉由建立基底類型的填充碼，和藉由將子執行個體作為參數傳遞至此基底填充碼類別的建構函式，基底成員的填充碼屬性可以進行存取。  
  
 例如，給定一個具有 `MyMethod` 執行個體方法和子類型 `MyChild` 的 `MyBase` 類別：  
  
```csharp  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 我們可以建立新的 `ShimMyBase` 填充碼來設定 `MyBase` 填充碼：  
  
```csharp  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 請注意，將子填充碼類型當作參數傳遞至基底填充碼建構函式時，會將子填充碼類型隱含轉換成子執行個體。  
  
 ShimMyChild 之產生的類型結構和 ShimMyBase 類似下列程式碼：  
  
```csharp  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a> 靜態建構函式  
 填充碼類型會公開靜態方法 `StaticConstructor`，藉此填充類型的靜態建構函式。 因為靜態建構函式只能執行一次，您必須在存取該類型的任何成員之前，確認已設定填充碼。  
  
###  <a name="BKMK_Finalizers"></a> 完成項  
 完成項在 Fakes 中並不支援。  
  
###  <a name="BKMK_Private_methods"></a> 私用方法  
 針對在簽章中只有可見類型的私用方法 (亦即可見的參數類型與傳回類型)，Fakes 程式碼產生器會建立這類私用方法的填充碼屬性。  
  
###  <a name="BKMK_Binding_interfaces"></a> 繫結介面  
 當已填充的類型實作介面時，程式碼產生器會發出允許同時繫結該介面所有成員的方法。  
  
 例如，給定一個實作 `IEnumerable<int>` 的 `MyClass` 類別：  
  
```csharp  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 我們可以藉由呼叫 Bind 方法填充在 MyClass 中的 `IEnumerable<int>` 實作：  
  
```csharp  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 ShimMyClass 之產生的類型結構類似下列程式碼：  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> 變更預設行為  
 每個產生的填充碼類別均會保留一個 `IShimBehavior` 介面的執行個體 (透過 `ShimBase<T>.InstanceBehavior` 屬性)。 每當用戶端呼叫沒有明確填充的執行個體成員時，便會使用此行為。  
  
 如果尚未明確設定此行為，則會使用靜態 `ShimsBehaviors.Current` 屬性所傳回的執行個體。 根據預設，這個屬性傳回的行為會擲回 `NotImplementedException` 例外狀況。  
  
 您隨時可以設定任何填充碼執行個體的 `InstanceBehavior` 屬性，藉以變更行為。 例如，下列程式碼片段會改變此填充碼為沒有任何動作或將傳回類型之預設值傳回的行為：  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 也可以針對所有已填充的執行個體 (其中尚未藉由設定靜態 `ShimsBehaviors.Current` 屬性來明確設定 `InstanceBehavior` 屬性) 對此行為全域變更：  
  
```csharp  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> 偵測環境存取  
 可附加行為至所有特定類型的成員，包含靜態方法，方法是藉由將 `ShimsBehaviors.NotImplemented` 行為指定為相對應填充碼類型的靜態屬性 `Behavior`：  
  
```csharp  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a>並行  
 填充碼類型適用於在 AppDomain 中的所有執行緒，且沒有執行緒相似性。 如果您打算使用可支援並行的測試執行器，這會是項重要的事實：涉及填充碼類型的測試不能同時執行。 這個屬性不是由 Fakes 執行階段強制設定的。  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> 從填充碼方法呼叫原始方法  
 假設我們驗證完傳遞給方法的檔案名稱之後，要在檔案系統實際寫入文字。 在這種情況下，我們可能會想要在填充碼方法中呼叫原始方法。  
  
 解決這個問題的第一個方式為使用委派和 `ShimsContext.ExecuteWithoutShims()` 包裝原始方法的呼叫，如下列程式碼所示：  
  
```csharp  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 另一種方式為設定此填充碼為 null，呼叫原始方法和還原此填充碼。  
  
```csharp  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter”);  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a> 限制  
 填充碼在來自 .NET 基底類別庫 **mscorlib** 和 **System** 的類型上並非全部都能使用。  
  
## <a name="external-resources"></a>外部資源  
  
### <a name="guidance"></a>指引  
 [使用 Visual Studio 2012 測試持續傳遞 - 第 2 章：單元測試：測試內部](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>請參閱  
 [使用 Microsoft Fakes 在測試期間隔離程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Peter Provost’s blog: Visual Studio 2012 Shims](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)  (Peter Provost 部落格︰Visual Studio 2012 填充碼)  
 [Video (1h16): Testing Un-testable Code with Fakes in Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837) (影片 (1 小時 16 分鐘)：在 Visual Studio 2012 中使用 Fakes 測試不可測試的程式碼)
