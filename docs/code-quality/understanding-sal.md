---
title: 了解 SAL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deb1825bb514afec4db3bf705ac787aadb88cc11
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="understanding-sal"></a>了解 SAL
Microsoft 原始程式碼註釋語言 (SAL) 提供一組註釋可讓您描述函式如何使用它的參數、 建立與其，相關的假設和完成時，它可保證。 標頭檔中定義的註解`<sal.h>`。 C + + 的 visual Studio 程式碼分析會使用 SAL 註釋，來修改其分析的函式。 用於 Windows 的驅動程式開發 SAL 2.0 的相關資訊，請參閱[SAL 2.0 註解的 Windows 驅動程式](http://go.microsoft.com/fwlink/?LinkId=250979)。  
  
 原生的 C 和 c + + 提供只有有限的方式，讓開發人員能夠一致地 express 的意圖，而且不變性。 藉由使用 SAL 註釋，您可以描述更詳細地函式，讓開發人員會使用它可更了解如何使用它們。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>什麼是 SAL，以及為什麼您應該使用它？  
 SAL 簡單的說，是讓您檢查您的程式碼編譯器經濟的方式。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL 可讓程式碼更有價值  
 SAL 可協助您讓您的程式碼設計更容易了解，以方便和程式碼分析工具。 請考量以下範例顯示 C 執行階段函式`memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 您可以判斷此函式的功能嗎？ 當實作或呼叫函式時，必須維護特定的屬性，以確保程式正確性。 只要查看宣告，例如此範例中，您不知道它們為何。 不含 SAL 註釋，您必須依賴文件或程式碼註解。 以下是什麼的 MSDN 文件的`memcpy`指出：  
  
> 「 複本計數位元組的 src 到目的地。 如果來源和目的地重疊，memcpy 的行為未定義。 您可以使用 memmove 處理重疊的區域。   
> **安全性注意事項：**確定目的地緩衝區是相同大小，等於或大於來源緩衝區。 如需詳細資訊，請參閱 「 避免緩衝區滿溢 」。  
  
 文件包含的資訊，建議您的程式碼必須維護特定的屬性，以確保程式的正確性的位元數：  
  
-   `memcpy` 複製`count`從來源緩衝區到目的緩衝區的位元組。  
  
-   目的緩衝區必須至少與來源緩衝區一樣大。  
  
 不過，編譯器無法讀取文件或非正式的註解。 它不知道兩個緩衝區之間沒有關聯性和`count`，和它也無法有效地猜測關聯性。 SAL 可以提供更清楚的內容和實作函式，如下所示：  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 請注意，這些註解類似於 MSDN 文件中的資訊，但它們是更簡潔，而且它們會遵照語意的模式。 當您讀取這段程式碼時，您可以快速了解此函數的屬性，以及如何避免緩衝區滿溢安全性問題。 更好的是，SAL 提供的語意模式可以改善效率與效能的潛在錯誤早期的探索中的自動程式碼分析工具。 想像一下，有人還是會撰寫這項錯誤實作`wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 這個實作包含常見的關閉一個錯誤。 幸運的是，程式碼作者包含 SAL 緩衝區大小註釋，程式碼分析工具可以藉由分析此單獨的函式攔截 bug。  
  
### <a name="sal-basics"></a>SAL 基本概念  
 SAL 定義四種基本參數，依使用方式模式分類。  
  
|分類|參數註釋|描述|  
|--------------|--------------------------|-----------------|  
|**輸入要呼叫函式**|`_In_`|資料傳遞至呼叫的函式，而且會被視為唯讀。|  
|**輸入呼叫函式，並輸出至呼叫端**|`_Inout_`|可用的資料傳遞至函式，並可能會修改。|  
|**呼叫端的輸出**|`_Out_`|呼叫端只會提供要寫入所呼叫函式的空間。 呼叫的函式會將資料寫入該空間。|  
|**指標至呼叫端的輸出**|`_Outptr_`|像**輸出至呼叫端**。 呼叫的函式所傳回的值是指標。|  
  
 這些四個基本的註解可以設為更明確以各種方式。 根據預設，註解式的指標參數會假設為必要，他們必須為非 NULL 函式才會成功。 基本的註解最常使用的變化表示指標參數為選擇性，如果它是 NULL，函式仍可以成功執行其工作。  
  
 下表顯示如何區分必要和選擇性參數：  
  
||參數為必要參數|參數是選擇性參數|  
|-|-----------------------------|-----------------------------|  
|**輸入要呼叫函式**|`_In_`|`_In_opt_`|  
|**輸入呼叫函式，並輸出至呼叫端**|`_Inout_`|`_Inout_opt_`|  
|**呼叫端的輸出**|`_Out_`|`_Out_opt_`|  
|**指標至呼叫端的輸出**|`_Outptr_`|`_Outptr_opt_`|  
  
 這些註解協助找出可能未初始化的值和型式和精確的方式使用無效的 null 指標。 將 NULL 傳遞至所需的參數可能會造成損毀，或它可能會導致傳回 「 已失敗 」 的錯誤程式碼。 無論如何，函式無法在此情況下它作業成功。  
  
## <a name="sal-examples"></a>SAL 範例  
 本節說明基本的 SAL 註釋的程式碼範例。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>使用 Visual Studio 程式碼分析工具找出缺失  
 在範例中，Visual Studio 程式碼分析工具搭配 SAL 註釋，以尋找程式碼缺失。 以下是如何執行此作業。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>若要使用 Visual Studio 程式碼分析工具和 SAL  
  
1.  在 Visual Studio 中，開啟包含 SAL 註釋的 c + + 專案。  
  
2.  在功能表列上選擇 **建置**，**針對方案執行程式碼分析**。  
  
     請考慮 _In\_本節中的範例。 如果您在其上執行程式碼分析，則會顯示這個警告：  
  
    > **C6387 無效的參數值**   
    > 'pInt' 可能是 '0': 這樣會違反函式 'InCallee' 的規格。  
  
### <a name="example-the-in-annotation"></a>範例： _In\_註釋  
 `_In_`附註會指出：  
  
-   參數必須是有效的而且將不會修改。  
  
-   此函式只會從單一項目緩衝區讀取。  
  
-   呼叫端必須提供緩衝區，並將它初始化。  
  
-   `_In_` 指定 「 唯讀 」。 常見的錯誤，將套用`_In_`參數應該具有`_Inout_`註解改為。  
  
-   `_In_` 但會忽略非指標純量上的分析器所允許的。  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 如果您使用 Visual Studio 程式碼分析，在此範例中，它會驗證呼叫端傳遞初始化緩衝區的非 Null 指標`pInt`。 在此情況下，`pInt`指標不能是 NULL。  
  
### <a name="example-the-inopt-annotation"></a>範例： _In_opt\_註釋  
 `_In_opt_` 等同於`_In_`，但輸入的參數可為 NULL，因此，此函式應該檢查此。  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證它存取緩衝區之前的函式將會檢查為 NULL。  
  
### <a name="example-the-out-annotation"></a>範例： _Out\_註釋  
 `_Out_` 支援常見的案例中傳入的項目緩衝區所指向的非 NULL 指標和函式會初始化項目。 呼叫端沒有呼叫; 之前將緩衝區初始化若要將它初始化，再傳回承諾呼叫的函式。  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio 程式碼分析工具會驗證呼叫端會將非 NULL 指標傳遞來的緩衝區`pInt`，再傳回，緩衝區由函式來初始化。  
  
### <a name="example-the-outopt-annotation"></a>範例： _Out_opt\_註釋  
 `_Out_opt_` 等同於`_Out_`，只不過參數可為 NULL，因此，此函式應該檢查此。  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證這個函數會檢查之前的 null`pInt`已取值，而且如果`pInt`不是 NULL，它會傳回之前，由函式來初始化緩衝區。  
  
### <a name="example-the-inout-annotation"></a>範例： _Inout\_註釋  
 `_Inout_` 用來標註函式可能會變更的指標參數。 滑鼠指標必須指向有效的初始化資料呼叫前，而且即使監視變更時，它必須在傳回時，仍然必須是有效的值。 註解會指定函式可能自由地從讀取與寫入一個項目緩衝區。 呼叫端必須提供緩衝區，並將它初始化。  
  
> [!NOTE]
>  像`_Out_`，`_Inout_`必須套用至可修改的值。  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證呼叫端傳遞非 NULL 指標，以初始化緩衝區`pInt`，而且，在傳回時之前,`pInt`仍然是非 null 緩衝區初始化。  
  
### <a name="example-the-inoutopt-annotation"></a>範例： _Inout_opt\_註釋  
 `_Inout_opt_` 等同於`_Inout_`，但輸入的參數可為 NULL，因此，此函式應該檢查此。  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證此函式檢查 null 存取緩衝區之前，以及是否`pInt`不是 NULL，它會傳回之前，由函式來初始化緩衝區。  
  
### <a name="example-the-outptr-annotation"></a>範例： _Outptr\_註釋  
 `_Outptr_` 用來標註的參數，要傳回的指標。  參數本身不能為 NULL，並呼叫的函式中傳回非 NULL 指標，該指標指向已初始化的資料。  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證呼叫端傳遞非 NULL 指標， `*pInt`，並在傳回緩衝區初始化函式。  
  
### <a name="example-the-outptropt-annotation"></a>範例： _Outptr_opt\_註釋  
 `_Outptr_opt_` 等同於`_Outptr_`，只不過是選擇性參數，呼叫端可以為 NULL 指標中傳遞的參數。  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證這個函數會檢查之前的 null`*pInt`已取值，而且再傳回，緩衝區由函式來初始化。  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>範例： _Success\_搭配 _Out 註釋\_  
 註解可以套用至大部分的物件。  特別是，您可以標註整體函式。  其中一個最明顯的特性函式的是可以成功或失敗。 但緩衝區和大小之間的關聯，例如 C/c + + 無法表示函式成功或失敗。 使用`_Success_`註釋，您可以說什麼函式成功的模樣。  參數以`_Success_`附註，則只要運算式，它為真時，表示已成功函式。 運算式可以是任何註解剖析器可以處理的項目。 函式成功時，才只適用於函式傳回後的註解的效果。 這個範例會示範如何`_Success_`互動`_Out_`執行正確的事。 您可以使用關鍵字`return`來表示的傳回值。  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_`註釋會使 Visual Studio 程式碼分析，以驗證呼叫端會將非 NULL 指標傳遞來的緩衝區`pInt`，並在傳回緩衝區初始化函式。  
  
## <a name="sal-best-practice"></a>SAL 最佳作法  
  
### <a name="adding-annotations-to-existing-code"></a>將註解加入至現有的程式碼  
 SAL 是功能強大的技術，可協助您提升的安全性和可靠性的程式碼。 您了解 SAL 之後，您可以套用到您的每日工作的新技術。 在新的程式碼，您可以使用 SAL 基礎規格所設計。在舊版的程式碼，您可以以累加方式加入註解，並藉此增加優點，每次您更新。  
  
 Microsoft 公用標頭必須已標註。 因此，我們建議，在專案中您第一次來標註分葉節點函式和函式，呼叫 Win32 Api 來取得最大效益。  
  
### <a name="when-do-i-annotate"></a>何時我加上註解？  
 以下是一些指導方針：  
  
-   標註所有指標參數。  
  
-   使程式碼分析可以確保緩衝區和指標的安全，加上註解值範圍的註解。  
  
-   標註鎖定規則和鎖定的副作用。 如需詳細資訊，請參閱[註釋鎖定行為](../code-quality/annotating-locking-behavior.md)。  
  
-   驅動程式內容和其他網域特定的屬性加上註解。  
  
 或所有參數，使您的意圖清除整個，並讓您輕鬆檢查已完成註解來標都註。  
  
## <a name="related-resources"></a>相關資源  
 [程式碼分析小組部落格](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 註釋減少 C/c + + 程式碼缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)