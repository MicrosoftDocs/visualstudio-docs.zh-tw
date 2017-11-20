---
title: "文字範本公用程式方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: "50"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 534a7317b4bca2abe559c028d025a52997a9f508
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="text-template-utility-methods"></a>文字範本公用程式方法
有數種方法，當您撰寫程式碼時，就一律可供您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文字範本。 這些方法會定義在<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
> [!TIP]
>  您也可以使用其他方法和規則 （不前置處理過後） 的文字範本中的主機環境所提供的服務。 例如，解決檔案路徑、 記錄錯誤，和取得服務所提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和載入任何套件。  如需詳細資訊，請參閱[從文字範本存取 Visual Studio](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4)。  
  
## <a name="write-methods"></a>撰寫方法  
 您可以使用`Write()`和`WriteLine()`將標準的程式碼區塊中，而不是使用運算式的程式碼區塊的文字附加的方法。 下列兩個程式碼區塊的功能相同。  
  
##### <a name="code-block-with-an-expression-block"></a>搭配運算式區塊的程式碼區塊  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>程式碼區塊使用 WriteLine()  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 您可能會發現它有用而不是運算式區塊的巢狀的控制結構冗長的程式碼區塊內使用其中一種公用程式方法。  
  
 `Write()`和`WriteLine()`方法有兩個多載，一個可接受單一字串參數，另一個接受複合格式字串以及要包含在字串中的物件陣列 (例如`Console.WriteLine()`方法)。 下列兩種用法`WriteLine()`相同的功能：  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## <a name="indentation-methods"></a>縮排方法  
 您可以使用縮排方法文字範本輸出的格式。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>類別具有`CurrentIndent`字串顯示目前的縮排文字範本中的屬性和`indentLengths`欄位也就是已加入縮排的清單。 您可以加入與縮排`PushIndent()`方法加號和減號縮排與`PopIndent()`方法。 如果您想要移除所有的縮排，使用`ClearIndent()`方法。 下列程式碼區塊顯示使用這些方法：  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 這個程式碼區塊會產生下列輸出：  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>錯誤和警告方法  
 您可以使用 錯誤和警告的公用程式方法新增訊息至[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]錯誤清單。 例如，下列程式碼會加入錯誤訊息 錯誤清單。  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## <a name="access-to-host-and-service-provider"></a>存取主應用程式和服務提供者  
 屬性`this.Host`可存取主機正在執行範本所公開的屬性。 若要使用`this.Host`，您必須設定`hostspecific`屬性`<@template#>`指示詞：  
  
 `<#@template ... hostspecific="true" #>`  
  
 型別`this.Host`範本正在執行的所在的主機類型而定。 在執行中的範本中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您可以轉型`this.Host`至`IServiceProvider`來存取服務，例如 IDE。 例如：  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>使用一組不同的公用程式方法  
 文字的產生程序的一部分，您的範本檔案會轉換成的類別，名稱永遠是`GeneratedTextTransformation`和繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。 如果您想要使用不同的一組方法相反地，您可以撰寫您自己的類別並指定範本指示詞中。 您的類別必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 使用`assembly`指示詞，以參考組件可以找到編譯的類別。