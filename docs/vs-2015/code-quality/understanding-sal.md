---
title: 瞭解 SAL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1c0129c6832c347e989b482acb2cf6ab9b80e60d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278449"
---
# <a name="understanding-sal"></a>了解 SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 原始程式碼批註語言 (SAL) 提供一組批註，可用來描述函式如何使用其參數、其對其所做的假設，以及完成時的保證。 批註會定義在標頭檔中 `<sal.h>` 。 適用于 c + + 的 Visual Studio 程式碼分析會使用 SAL 注釋來修改其函數分析。 如需有關 Windows 驅動程式開發之 SAL 2.0 的詳細資訊，請參閱 [Windows 驅動程式的 sal 2.0 批註](https://msdn.microsoft.com/library/windows/hardware/hh454237.aspx)。  
  
 C 和 c + + 原生只提供有限的方式，讓開發人員可以一致地表達意圖和 invariance。 藉由使用 SAL 注釋，您可以更詳細地描述您的函式，讓取用這些函式的開發人員可以更清楚地瞭解其使用方式。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>什麼是 SAL，為什麼要使用它？  
 單純地說，SAL 是讓編譯器為您檢查程式碼的低成本方式。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL 讓程式碼更具價值  
 SAL 可協助您讓程式碼設計更容易理解，適用于人類和程式碼分析工具。 請看看下列範例，其中顯示 C 執行時間函式 `memcpy` ：  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 您可以知道此函式的功能是什麼？ 執行或呼叫函式時，必須維護某些屬性，以確保程式的正確性。 只要查看範例中的宣告，就不知道它們是什麼。 如果沒有 SAL 注釋，您就必須依賴檔或程式碼批註。 以下是 MSDN 檔的說明 `memcpy` ：  
  
> "將 src 的計數位節複製到目的地。 如果來源和目的地重迭，則 memcpy 的行為是未定義的。 使用 memmove 來處理重迭的區域。   
> **安全性注意事項：** 請確定目的地緩衝區的大小等於或大於來源緩衝區。 如需詳細資訊，請參閱避免緩衝區溢位。  
  
 檔中包含幾個部分的資訊，建議您的程式碼必須維護某些屬性，以確保程式的正確性：  
  
- `memcpy``count`從來源緩衝區將位元組的複製到目的緩衝區。  
  
- 目的地緩衝區必須至少與來源緩衝區一樣大。  
  
  不過，編譯器無法讀取檔或非正式批註。 這並不知道這兩個緩衝區之間有關聯性 `count` ，而且也無法有效地猜測關聯性。 SAL 可以更清楚地瞭解函式的屬性和執行，如下所示：  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 請注意，這些批註類似于 MSDN 檔中的資訊，但它們比較簡潔，並遵循語義模式。 當您閱讀此程式碼時，可以快速瞭解此函式的屬性，以及如何避免緩衝區溢位的安全性問題。 更棒的是，SAL 提供的語義模式可以改善自動化程式碼分析工具在早期探索潛在錯誤的效率和效益。 假設有人寫了這個錯誤的實作為 `wmemcpy` ：  
  
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
  
 這項實行包含共通的非同一個錯誤。 幸運的是，程式碼作者包含 SAL 緩衝區大小注釋，而程式碼分析工具可以單獨分析此函式來攔截 bug。  
  
### <a name="sal-basics"></a>SAL 基本概念  
 SAL 定義四種基本的參數，這些都是依使用模式分類。  
  
|類別|參數注釋|說明|  
|--------------|--------------------------|-----------------|  
|**輸入至呼叫的函式**|`_In_`|資料會傳遞至呼叫的函式，並被視為唯讀。|  
|**輸入至呼叫的函式，並輸出至呼叫端**|`_Inout_`|可用的資料會傳遞至函式中，而且可能會遭到修改。|  
|**輸出至呼叫端**|`_Out_`|呼叫端只會提供要寫入之被呼叫函式的空間。 呼叫的函式會將資料寫入該空間。|  
|**呼叫端指標的輸出**|`_Outptr_`|如同 **輸出至呼叫**端。 呼叫的函式所傳回的值是指標。|  
  
 這四個基本批註在各種方面都可以更明確地進行。 根據預設，批註的指標參數是必要的，它們必須是非 Null，函式才能成功。 基本批註最常使用的變化表示指標參數是選擇性的，如果是 Null，則函式仍然可以成功執行其工作。  
  
 下表說明如何區分必要參數和選擇性參數：  
  
||需要參數|參數是選擇性的|  
|-|-----------------------------|-----------------------------|  
|**輸入至呼叫的函式**|`_In_`|`_In_opt_`|  
|**輸入至呼叫的函式，並輸出至呼叫端**|`_Inout_`|`_Inout_opt_`|  
|**輸出至呼叫端**|`_Out_`|`_Out_opt_`|  
|**呼叫端指標的輸出**|`_Outptr_`|`_Outptr_opt_`|  
  
 這些批註有助於找出可能未初始化的值，以及不正確 null 指標以正式且精確的方式使用。 將 Null 傳遞至必要的參數可能會造成損毀，或可能會導致傳回「失敗」錯誤碼。 這兩種方式都不會在執行作業時成功。  
  
## <a name="sal-examples"></a>SAL 範例  
 本節說明基本 SAL 注釋的程式碼範例。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>使用 Visual Studio Code 分析工具尋找瑕疵  
 在範例中，Visual Studio Code 分析工具會與 SAL 注釋一起使用，以找出程式碼缺失。 方法如下所示。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>使用 Visual Studio 程式碼分析工具和 SAL  
  
1. 在 Visual Studio 中，開啟包含 SAL 注釋的 c + + 專案。  
  
2. 在功能表列上，選擇 [ **組建**]、[ **針對方案執行程式碼分析**]。  
  
    請考慮本節 \_ 中的 \_ 範例。 如果您對其執行程式碼分析，則會顯示此警告：  
  
   > **C6387 不正確參數值**   
   > ' 啤酒 ' 可能是 ' 0 '：這不符合函數 ' InCallee ' 的規格。  
  
### <a name="example-the-_in_-annotation"></a>範例： \_ In \_ 批註  
 `_In_`批註指出：  
  
- 參數必須是有效的，而且不會修改。  
  
- 函式只會讀取單一元素的緩衝區。  
  
- 呼叫端必須提供緩衝區，並將其初始化。  
  
- `_In_` 指定「唯讀」。 常見的錯誤是套用 `_In_` 至應該 `_Inout_` 改用批註的參數。  
  
- `_In_` 在非指標純量上，分析器會允許但不會忽略。  
  
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
  
 如果您在此範例中使用 Visual Studio Code 分析，它會驗證呼叫端是否將非 Null 指標傳遞給的初始化緩衝區 `pInt` 。 在此情況下， `pInt` 指標不可以是 Null。  
  
### <a name="example-the-_in_opt_-annotation"></a>範例： \_ In_opt \_ 注釋  
 `_In_opt_` 與相同 `_In_` ，不同之處在于輸入參數允許為 Null，因此，函式應該檢查是否有此值。  
  
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
  
 Visual Studio Code 分析會驗證函式在存取緩衝區之前，會檢查是否有 Null。  
  
### <a name="example-the-_out_-annotation"></a>範例： \_ Out \_ 注釋  
 `_Out_` 支援常見的案例，其中會傳入指向專案緩衝區的非 Null 指標，且函式會初始化元素。 呼叫端不需要在呼叫之前初始化緩衝區;呼叫的函式承諾在傳回之前將它初始化。  
  
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
  
 Visual Studio Code 分析工具會驗證呼叫端是否將非 Null 指標傳遞給的緩衝區 `pInt` ，而且緩衝區會在傳回之前由函式初始化。  
  
### <a name="example-the-_out_opt_-annotation"></a>範例： \_ Out_opt \_ 注釋  
 `_Out_opt_` 與相同 `_Out_` ，不同之處在于參數允許為 Null，因此，函式應該檢查這個。  
  
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
  
 Visual Studio Code 分析會驗證此函式在取值之前檢查是否為 Null，而且如果不是 Null，則會在函式傳回 `pInt` `pInt` 之前，先將緩衝區初始化。  
  
### <a name="example-the-_inout_-annotation"></a>範例： \_ Inout \_ 注釋  
 `_Inout_` 用來標注函式可能變更的指標參數。 指標必須在呼叫之前指向有效的已初始化資料，即使它有變更，在傳回時仍必須有有效值。 批註會指定函式可以自由地讀取和寫入至單一元素的緩衝區。 呼叫端必須提供緩衝區，並將其初始化。  
  
> [!NOTE]
> 如同 `_Out_` ， `_Inout_` 必須套用至可修改的值。  
  
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
  
 Visual Studio Code 分析會驗證呼叫端是否將非 Null 指標傳遞給的初始化緩衝區 `pInt` ，而且在傳回之前， `pInt` 仍非 null 且緩衝區已初始化。  
  
### <a name="example-the-_inout_opt_-annotation"></a>範例： \_ Inout_opt \_ 注釋  
 `_Inout_opt_` 與相同 `_Inout_` ，不同之處在于輸入參數允許為 Null，因此，函式應該檢查是否有此值。  
  
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
  
 Visual Studio Code 分析會驗證此函式在存取緩衝區之前會先檢查是否有 Null，如果不是 Null，則會在函式傳回 `pInt` 之前，先將緩衝區初始化。  
  
### <a name="example-the-_outptr_-annotation"></a>範例： \_ Outptr \_ 批註  
 `_Outptr_` 用來標注要傳回指標的參數。  參數本身不應為 Null，且所呼叫的函式會傳回非 Null 指標，且該指標指向已初始化的資料。  
  
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
  
 Visual Studio Code 分析會驗證呼叫端是否傳遞的非 Null 指標 `*pInt` ，且該緩衝區會在傳回之前由函式初始化。  
  
### <a name="example-the-_outptr_opt_-annotation"></a>範例： \_ Outptr_opt \_ 注釋  
 `_Outptr_opt_` 與相同 `_Outptr_` ，不同之處在于參數是選擇性的，而呼叫端可以傳入參數的 Null 指標。  
  
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
  
 Visual Studio Code 分析會驗證此函式在取值之前會先檢查是否為 Null `*pInt` ，而且緩衝區會在傳回之前由函式初始化。  
  
### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>範例： \_ \_ 結合 Out 的 Success 注釋 \_\_  
 批註可以套用至大部分的物件。  尤其是，您可以為整個函式加上批註。  最明顯的函式特性之一，就是它可以成功或失敗。 但是，如同緩衝區與其大小之間的關聯，C/c + + 無法表達函數成功或失敗。 藉由使用 `_Success_` 批註，您可以說出函式的成功外觀。  批註的參數 `_Success_` 只是一個運算式，表示函式已成功。 此運算式可以是注釋剖析器可以處理的任何事物。 在函式傳回之後，批註的效果僅適用于函數成功時。 這個範例會示範如何 `_Success_` 與互動 `_Out_` 以進行正確的動作。 您可以使用關鍵字 `return` 來代表傳回值。  
  
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
  
 `_Out_`批註會導致 Visual Studio Code 分析，以驗證呼叫端是否將非 Null 指標傳遞給的緩衝區 `pInt` ，而且緩衝區會在傳回之前由函式初始化。  
  
## <a name="sal-best-practice"></a>SAL 最佳作法  
  
### <a name="adding-annotations-to-existing-code"></a>將批註新增至現有的程式碼  
 SAL 是一項功能強大的技術，可協助您提升程式碼的安全性和可靠性。 瞭解 SAL 之後，您可以將新的技能套用至您的每日工作。 在新的程式碼中，您可以在整個設計中使用以 SAL 為基礎的規格;在較舊的程式碼中，您可以在每次更新時，以累加方式新增批註，進而增加各項權益。  
  
 Microsoft 公用標頭已批註。 因此，我們建議您在您的專案中，先標注分葉節點函式和函式，以呼叫 Win32 Api 來取得最大效益。  
  
### <a name="when-do-i-annotate"></a>何時會加上批註？  
 以下是一些指導方針：  
  
- 標注所有指標參數。  
  
- 標注值範圍批註，讓程式碼分析可以確保緩衝區和指標的安全。  
  
- 標注鎖定規則和鎖定副作用。 如需詳細資訊，請參閱 [批註鎖定行為](../code-quality/annotating-locking-behavior.md)。  
  
- 標注驅動程式屬性和其他網域特定屬性。  
  
  或者，您可以為所有參數加上批註，讓您的意圖清楚明瞭，並讓您輕鬆檢查批註是否已完成。  
  
## <a name="related-resources"></a>相關資源  
 [程式碼分析小組的 Blog](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/c + + 程式碼瑕疵](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [標注函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [標注函式行為](../code-quality/annotating-function-behavior.md)   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用注釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
