---
title: 了解 SAL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 847631d28febe81be2e688b7c643ed1f4cfcba18
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945953"
---
# <a name="understanding-sal"></a>了解 SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 原始程式碼註釋語言 (SAL) 提供一組註釋，您可以使用來描述函式會使用其參數、 它對它們的假設和完成時的保證。 標頭檔中所定義的註解`<sal.h>`。 C + + 的 visual Studio 程式碼分析會修改其分析的函式中使用 SAL 註釋。 適用於 Windows 的驅動程式開發 SAL 2.0 的相關資訊，請參閱[SAL 2.0 註解的 Windows 驅動程式](http://go.microsoft.com/fwlink/?LinkId=250979)。  
  
 原生，C 和 c + + 提供適用於開發人員一致的方式表達意圖和不可變數只有有限的方式。 藉由使用 SAL 註釋中,，您可以描述您的函式，更詳細地使開發人員使用它們可以更了解如何使用它們。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>什麼是 SAL 以及為什麼您應該使用它？  
 SAL 簡單的說，是經濟的方式，讓編譯器為您檢查您的程式碼。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL 讓程式碼更有價值  
 SAL 可協助您讓您的程式碼設計更容易了解，讓人和程式碼分析工具。 此範例會顯示 C 執行階段函式，請考慮`memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 您可以判斷此函式的功能嗎？ 當實作或呼叫函式時，必須維護特定屬性，以確保程式正確性。 只要查看宣告，例如範例中，您不知道是什麼。 不含 SAL 註釋，您必須依賴文件或程式碼註解。 以下是哪些 MSDN 文件`memcpy`說：  
  
> 「 複本計數的 src 到目的地的位元組。 如果來源和目的地重疊，memcpy 的行為是未定義的。 您可以使用 memmove 處理重疊的區域。   
> **安全性注意事項：** 確定目的地緩衝區與來源緩衝區是相同大小，或大於來源緩衝區。 如需詳細資訊，請參閱 「 避免緩衝區滿溢 」。  
  
 文件包含幾個建議，您的程式碼必須維護特定的屬性，以確保程式正確性資訊位元：  
  
- `memcpy` 複製`count`的位元組從來源緩衝區複製到目的緩衝區。  
  
- 目的緩衝區必須至少與來源緩衝區一樣大。  
  
  不過，編譯器無法讀取文件或非正式的註解。 它並不知道兩個緩衝區之間沒有關聯性和`count`，它也無法有效地猜發生了解關聯性。 SAL 可以提供更清楚的內容和實作的函式，如下所示：  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 請注意這些註解類似的 MSDN 文件中的資訊，但它們是更為精簡，而且它們會遵循語意的模式。 當您閱讀這段程式碼時，您可以快速了解此函式的屬性，以及如何避免緩衝區滿溢安全性問題。 更棒的是，SAL 提供的語意模式可以改善效率與效能的潛在錯誤的早期探索中的自動程式碼分析工具。 假設有人撰寫這個不良實作`wmemcpy`:  
  
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
  
 這項實作包含常見的關閉一個錯誤。 幸運的是，程式碼作者包含 SAL 緩衝區大小註釋，程式碼分析工具可以藉由分析此函式會獨自攔截錯誤。  
  
### <a name="sal-basics"></a>SAL 基本概念  
 SAL 定義四種基本依使用量模式分類的參數。  
  
|分類|參數註釋|描述|  
|--------------|--------------------------|-----------------|  
|**輸入要呼叫的函式**|`_In_`|資料會傳遞至呼叫的函式，並以唯讀狀態，都會被視為。|  
|**輸入呼叫函式，並輸出至呼叫端**|`_Inout_`|可用的資料會傳遞至函式，並可能遭到修改。|  
|**呼叫端的輸出**|`_Out_`|呼叫端只會提供要寫入所呼叫函式的空間。 呼叫的函式會將資料寫入該空間。|  
|**指標，呼叫端的輸出**|`_Outptr_`|像是**的輸出傳送至呼叫端**。 呼叫的函式所傳回的值是指標。|  
  
 這些四個基本的註解可以設為更明確以各種方式。 根據預設，註解式的指標參數會假設為必要，他們必須為非 NULL 函式才會成功。 基本的註解的最常用的變化表示的指標參數為選擇性，如果它是 NULL，函式仍可以成功執行其工作。  
  
 此表顯示如何區分必要和選擇性參數：  
  
||都是必要參數|參數是選擇性參數|  
|-|-----------------------------|-----------------------------|  
|**輸入要呼叫的函式**|`_In_`|`_In_opt_`|  
|**輸入呼叫函式，並輸出至呼叫端**|`_Inout_`|`_Inout_opt_`|  
|**呼叫端的輸出**|`_Out_`|`_Out_opt_`|  
|**指標，呼叫端的輸出**|`_Outptr_`|`_Outptr_opt_`|  
  
 這些註解協助您識別可能未初始化的值和無效的 null 指標會使用型式和精確的方式。 將 NULL 傳遞到必要的參數可能會造成當機，或它可能會導致傳回 「 已失敗 」 的錯誤程式碼。 無論如何，函式不能在執行其工作成功。  
  
## <a name="sal-examples"></a>SAL 範例  
 此區段會顯示基本的 SAL 註釋的程式碼範例。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>使用 Visual Studio 程式碼分析工具找出缺陷錯誤  
 在範例中，Visual Studio 程式碼分析工具搭配 SAL 註釋，以尋找程式碼缺失。 以下是如何執行該動作。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>若要使用 Visual Studio 程式碼分析工具和 SAL  
  
1. 在 Visual Studio 中，開啟包含 SAL 註釋的 c + + 專案。  
  
2. 在功能表列上選擇 **建置**，**針對方案執行程式碼分析**。  
  
    請考慮\_在\_這一節的範例。 如果您在其上執行程式碼分析，會顯示此警告：  
  
   > **C6387 無效的參數值**   
   > 'pInt' 可能是 '0': 這不會遵守 'InCallee' 函式規格。  
  
### <a name="example-the-in-annotation"></a>範例：\_在\_註釋  
 `_In_`註解表示：  
  
-   參數必須有效，而且將不會修改。  
  
-   此函式只會從單一項目緩衝區讀取。  
  
-   呼叫端必須提供緩衝區，並將它初始化。  
  
-   `_In_` 指定 「 唯讀 」。 常見的錯誤是套用`_In_`應有的參數`_Inout_`註釋改。  
  
-   `_In_` 但會忽略非指標純量上分析器所允許的。  
  
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
  
 如果您使用 Visual Studio 程式碼分析，在此範例中，它會驗證呼叫端傳遞非 Null 指標，來初始化緩衝區`pInt`。 在此情況下，`pInt`指標不能是 NULL。  
  
### <a name="example-the-inopt-annotation"></a>範例：\_In_opt\_註釋  
 `_In_opt_` 等同於`_In_`，差異在於允許的輸入的參數是 NULL，因此，此函式應該檢查這個。  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析驗證才能存取緩衝區的函式將會檢查 null。  
  
### <a name="example-the-out-annotation"></a>範例：\_出\_註釋  
 `_Out_` 支援常見的案例，在其中傳入指向的項目緩衝區的非 NULL 指標和函式會初始化項目。 呼叫端沒有呼叫; 之前將緩衝區初始化將它初始化，它會傳回前能夠呼叫的函式。  
  
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
  
 Visual Studio 程式碼分析工具會驗證呼叫端傳遞非 NULL 指標，如緩衝區`pInt`，它會傳回之前將緩衝區初始化函式。  
  
### <a name="example-the-outopt-annotation"></a>範例：\_Out_opt\_註釋  
 `_Out_opt_` 等同於`_Out_`，差異在於參數可為 NULL，因此，此函式應該檢查這個。  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證這個函數會檢查 null 之前`pInt`已取值，而且如果`pInt`不是 NULL，它會傳回之前，由函式來初始化緩衝區。  
  
### <a name="example-the-inout-annotation"></a>範例：\_Inout\_註釋  
 `_Inout_` 用來加上註解可能會變更函式的指標參數。 滑鼠指標必須指向有效的初始化資料呼叫前，，即使它會變更，它必須在傳回時，仍有有效的值。 註解會指定函式可以自由的讀取和寫入至其中一個元素的緩衝區。 呼叫端必須提供緩衝區，並將它初始化。  
  
> [!NOTE]
>  像是`_Out_`，`_Inout_`必須套用至可修改的值。  
  
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
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Visual Studio 程式碼分析可讓您驗證呼叫端傳遞非 NULL 指標，來初始化緩衝區`pInt`，而且，在傳回時之前,`pInt`仍然是非 null 並將緩衝區初始化。  
  
### <a name="example-the-inoutopt-annotation"></a>範例：\_Inout_opt\_註釋  
 `_Inout_opt_` 等同於`_Inout_`，差異在於允許的輸入的參數是 NULL，因此，此函式應該檢查這個。  
  
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
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證它所存取之緩衝區之前，而且如果此函式將會檢查 null`pInt`不是 NULL，它會傳回之前，由函式來初始化緩衝區。  
  
### <a name="example-the-outptr-annotation"></a>範例：\_Outptr\_註釋  
 `_Outptr_` 用來標註的參數，目的是要傳回的指標。  參數本身不能為 NULL，並呼叫的函式中傳回非 NULL 指標，該指標指向已初始化的資料。  
  
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
  
 Visual Studio 程式碼分析可讓您驗證呼叫端傳遞非 NULL 指標， `*pInt`，而且它會傳回之前將緩衝區初始化函式。  
  
### <a name="example-the-outptropt-annotation"></a>範例：\_Outptr_opt\_註釋  
 `_Outptr_opt_` 等同於`_Outptr_`，只不過是選擇性參數，呼叫端可以為參數傳遞 NULL 指標。  
  
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
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio 程式碼分析會驗證這個函數會檢查之前的 null`*pInt`已取值，而且它會傳回之前將緩衝區初始化函式。  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>範例：\_成功\_結合的註解\_出\_  
 註解可以套用至大部分的物件。  特別是，您可以標註的整個函式。  其中一個函式的最明顯的特性是它可以成功或失敗。 但緩衝區和大小之間的關聯，例如 C/c + + 無法表示函式成功或失敗。 使用`_Success_`註解，您可以說出成功的函式如下所示。  參數以`_Success_`註釋不只是，當為 true 表示已成功函式的運算式。 運算式可以是任何註解剖析器可以處理的項目。 函式成功時，都只適用於函式傳回之後的註釋的效果。 此範例示範如何`_Success_`互動`_Out_`執行適當的動作。 您可以使用關鍵字`return`來代表傳回的值。  
  
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
  
 `_Out_`註釋會導致 Visual Studio 程式碼分析，來驗證呼叫端傳遞非 NULL 指標，如緩衝區`pInt`，而且它會傳回之前將緩衝區初始化函式。  
  
## <a name="sal-best-practice"></a>SAL 最佳作法  
  
### <a name="adding-annotations-to-existing-code"></a>將註解加入至現有的程式碼  
 SAL 是一種功能強大的技術，可協助您提升的安全性和可靠性的程式碼。 您將了解 SAL 之後，您可以套用到您的每日工作的新技能。 在新的程式碼，您可以使用 SAL 型規格; 整個設計在舊版的程式碼，您可以以累加方式新增註解，並每次您更新，進而提升的優點。  
  
 Microsoft 公用標頭已標註。 因此，我們建議，在您的專案中您第一次標註分葉節點函式和函式，呼叫 Win32 Api 來取得最大效益。  
  
### <a name="when-do-i-annotate"></a>何時我加上註解？  
 以下是一些指導方針：  
  
- 所有的指標參數加上註解。  
  
- 使程式碼分析，才能確保緩衝區和指標的安全性，加上註解的值範圍的註解。  
  
- 標註鎖定規則和鎖定的副作用。 如需詳細資訊，請參閱 <<c0> [ 註釋鎖定行為](../code-quality/annotating-locking-behavior.md)。  
  
- 驅動程式屬性和其他網域特有的屬性加上註解。  
  
  或者，您可以標註，使整個您意圖清除，並讓您輕鬆查看註解，完成所有的參數。  
  
## <a name="related-resources"></a>相關資源  
 [程式碼分析小組部落格](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 註釋減少 C/c + + 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
