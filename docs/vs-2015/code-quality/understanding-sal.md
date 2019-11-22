---
title: 瞭解 SAL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c8f29a909f6aef75976a551546d4cbeafdf03b37
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291875"
---
# <a name="understanding-sal"></a>了解 SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 原始程式碼注釋語言（SAL）提供一組批註，您可以用來描述函式如何使用其參數、其相關假設，以及它在完成時所進行的保證。 批註會定義在標頭檔中 `<sal.h>`。 Visual Studio 的程式C++代碼分析會使用 SAL 注釋來修改其函式的分析。 如需有關 SAL 2.0 以進行 Windows 驅動程式開發的詳細資訊，請參閱[適用于 Windows 驅動程式的 sal 2.0 注釋](https://go.microsoft.com/fwlink/?LinkId=250979)。  
  
 在原生、 C++ C 和中，僅提供有限的方式讓開發人員一致地表達意圖和 invariance。 藉由使用 SAL 注釋，您可以更詳細地描述您的函式，讓使用它們的開發人員可以更瞭解如何使用它們。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>什麼是 SAL，為什麼要使用它？  
 單純地說，SAL 是讓編譯器為您檢查程式碼的一種經濟實惠的方式。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL 讓程式碼更有價值  
 SAL 可協助您讓程式碼設計更容易理解，適用于人類和程式碼分析工具。 請考慮下列範例，其中會顯示 `memcpy`的 C 執行時間函數：  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 您可以分辨此函式的作用嗎？ 執行或呼叫函式時，必須維護某些屬性，以確保程式的正確性。 只要查看範例中的宣告，您就不知道它們是什麼。 如果沒有 SAL 注釋，您就必須依賴檔或程式碼批註。 以下是 `memcpy` 的 MSDN 檔說明：  
  
> 「將 src 的計數位節複製到目的地。 如果來源和目的地重迭，memcpy 的行為會是未定義的。 使用 memmove 來處理重迭的區域。   
> **安全性注意事項：** 請確定目的地緩衝區的大小等於或大於來源緩衝區。 如需詳細資訊，請參閱避免緩衝區溢位。  
  
 檔包含幾個部分的資訊，建議您的程式碼必須維護特定屬性，以確保程式的正確性：  
  
- `memcpy` 會將位元組的 `count` 從來源緩衝區複製到目的地緩衝區。  
  
- 目的緩衝區必須至少與來源緩衝區一樣大。  
  
  不過，編譯器無法讀取檔或非正式批註。 這並不知道這兩個緩衝區和 `count`之間有關聯性，而且也無法有效地猜測關聯性。 SAL 可以更清楚地瞭解函式的屬性和實作用，如下所示：  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 請注意，這些批註與 MSDN 檔中的資訊類似，但它們比較簡潔，而且遵循語義模式。 當您閱讀此程式碼時，您可以快速瞭解此函式的屬性，以及如何避免緩衝區溢位的安全性問題。 更棒的是，SAL 提供的語義模式可以改善自動化程式碼分析工具在早期探索潛在 bug 時的效率和效率。 假設有人寫了這個 `wmemcpy`的錯誤執行：  
  
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
  
 此實作為包含常見的不同錯誤。 幸運的是，程式碼作者包含 SAL 緩衝區大小注釋，程式碼分析工具可以單獨分析此函數來攔截 bug。  
  
### <a name="sal-basics"></a>SAL 基本概念  
 SAL 定義四種基本類型的參數，依使用模式分類。  
  
|類別|參數注釋|描述|  
|--------------|--------------------------|-----------------|  
|**輸入至呼叫的函式**|`_In_`|資料會傳遞至所呼叫的函式，並被視為唯讀。|  
|**輸入至所呼叫的函式，並輸出至呼叫端**|`_Inout_`|可用的資料會傳遞至函式中，而且可能會遭到修改。|  
|**輸出至呼叫端**|`_Out_`|呼叫端只會為要寫入的呼叫函式提供空間。 被呼叫的函式會將資料寫入該空間。|  
|**呼叫端指標的輸出**|`_Outptr_`|Like**輸出至呼叫**端。 所呼叫函式所傳回的值是指標。|  
  
 這四個基本批註可以透過各種方式來進行更明確的。 根據預設，批註的指標參數會假設為必要--它們必須為非 Null，函式才會成功。 基本注釋最常使用的變化表示指標參數是選擇性的，如果它是 Null，函式仍然可以成功執行其工作。  
  
 下表顯示如何區別必要和選擇性的參數：  
  
||需要參數|參數是選擇性的|  
|-|-----------------------------|-----------------------------|  
|**輸入至呼叫的函式**|`_In_`|`_In_opt_`|  
|**輸入至所呼叫的函式，並輸出至呼叫端**|`_Inout_`|`_Inout_opt_`|  
|**輸出至呼叫端**|`_Out_`|`_Out_opt_`|  
|**呼叫端指標的輸出**|`_Outptr_`|`_Outptr_opt_`|  
  
 這些批註有助於找出可能未初始化的值，而不正確 null 指標會以正式且正確的方式使用。 將 Null 傳遞給必要的參數可能會導致當機，或可能會導致傳回「失敗」的錯誤碼。 無論如何，函式都無法成功執行其作業。  
  
## <a name="sal-examples"></a>SAL 範例  
 本節顯示基本 SAL 注釋的程式碼範例。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>使用 Visual Studio Code 分析工具來尋找瑕疵  
 在範例中，Visual Studio Code 分析工具會與 SAL 注釋一起使用，以找出程式碼缺失。 以下是如何執行此動作的方法。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>若要使用 Visual Studio 程式碼分析工具和 SAL  
  
1. 在 Visual Studio 中，開啟C++包含 SAL 注釋的專案。  
  
2. 在功能表列上，選擇 [**組建**]、[**針對方案執行程式碼分析**]。  
  
    請考慮本節中\_ 範例中的 \_。 如果您對其執行程式碼分析，則會顯示此警告：  
  
   > **C6387 不正確參數值**   
   > ' pInt ' 可以是 ' 0 '：這不符合函數 ' InCallee ' 的規格。  
  
### <a name="example-the-_in_-annotation"></a>範例：\_ 注釋中的 \_  
 `_In_` 注釋指出：  
  
- 參數必須有效，而且不會修改。  
  
- 函式只會從單一元素緩衝區讀取。  
  
- 呼叫端必須提供緩衝區，並將它初始化。  
  
- `_In_` 指定「唯讀」。 常見的錯誤是將 `_In_` 套用至應改為使用 `_Inout_` 注釋的參數。  
  
- `_In_` 是允許的，但分析器會在非指標純量上忽略。  
  
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
  
 如果您在此範例上使用 Visual Studio Code 分析，它會驗證呼叫端會將非 Null 指標傳遞給 `pInt`的初始化緩衝區。 在此情況下，`pInt` 指標不可以是 Null。  
  
### <a name="example-the-_in_opt_-annotation"></a>範例： \_In_opt\_ 注釋  
 `_In_opt_` 與 `_In_`相同，不同之處在于輸入參數允許為 Null，因此函式應該檢查是否有此。  
  
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
  
 Visual Studio Code 分析會驗證函式會先檢查是否有 Null，然後再存取緩衝區。  
  
### <a name="example-the-_out_-annotation"></a>範例： \_Out\_ 注釋  
 `_Out_` 支援一種常見的案例，其中指向元素緩衝區的非 Null 指標會傳入，而函式會初始化專案。 呼叫端不需要在呼叫之前初始化緩衝區。被呼叫的函式會承諾在傳回之前將它初始化。  
  
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
  
 Visual Studio Code 分析工具會驗證呼叫端是否將非 Null 指標傳遞給 `pInt` 的緩衝區，並在函式傳回之前，由函式初始化緩衝區。  
  
### <a name="example-the-_out_opt_-annotation"></a>範例： \_Out_opt\_ 注釋  
 `_Out_opt_` 與 `_Out_`相同，不同之處在于參數允許為 Null，因此函式應該檢查是否有此。  
  
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
  
 Visual Studio Code 分析會驗證此函式在 `pInt` 被取值之前檢查是否有 Null，如果 `pInt` 不是 Null，則會在傳回之前由函式初始化緩衝區。  
  
### <a name="example-the-_inout_-annotation"></a>範例： \_Inout\_ 注釋  
 `_Inout_` 可用來標注函式可能變更的指標參數。 指標必須在呼叫之前指向有效的初始化資料，即使它有變更，它仍必須具有傳回的有效值。 批註會指定函式可以自由地讀取和寫入單一元素緩衝區。 呼叫端必須提供緩衝區，並將它初始化。  
  
> [!NOTE]
> 如同 `_Out_`，`_Inout_` 必須套用至可修改的值。  
  
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
  
 Visual Studio Code 分析會驗證呼叫端是否將非 Null 指標傳遞給 `pInt`的初始化緩衝區，而且在傳回之前，`pInt` 仍為非 Null 且緩衝區已初始化。  
  
### <a name="example-the-_inout_opt_-annotation"></a>範例： \_Inout_opt\_ 注釋  
 `_Inout_opt_` 與 `_Inout_`相同，不同之處在于輸入參數允許為 Null，因此函式應該檢查是否有此。  
  
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
  
 Visual Studio Code 分析會驗證此函式在存取緩衝區之前檢查是否有 Null，如果 `pInt` 不是 Null，則會在函式傳回之前，先初始化緩衝區。  
  
### <a name="example-the-_outptr_-annotation"></a>範例： \_Outptr\_ 注釋  
 `_Outptr_` 可用來標注用於傳回指標的參數。  參數本身不應為 Null，而且被呼叫的函式會在其中傳回非 Null 指標，而該指標會指向已初始化的資料。  
  
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
  
 Visual Studio Code 分析會驗證呼叫端是否為 `*pInt`傳遞非 Null 指標，以及函式在傳回之前是否已初始化緩衝區。  
  
### <a name="example-the-_outptr_opt_-annotation"></a>範例： \_Outptr_opt\_ 注釋  
 `_Outptr_opt_` 與 `_Outptr_`相同，不同之處在于參數是選擇性的，呼叫者可以傳入參數的 Null 指標。  
  
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
  
 Visual Studio Code 分析會驗證此函式會先檢查是否有 Null，再取值 `*pInt`，而且該緩衝區會在傳回之前由函式初始化。  
  
### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>範例： \_成功\_ 注釋與 \_Out 的結合\_  
 批註可以套用至大部分的物件。  特別是，您可以標注整個函式。  函式最明顯的特性之一，就是它可以成功或失敗。 但是就像緩衝區和其大小之間的關聯，C/C++無法表示函數成功或失敗。 藉由使用 `_Success_` 注釋，您可以說函式的成功外觀。  `_Success_` 注釋的參數只是一個運算式，其為 true 時，表示函數已成功。 運算式可以是批註剖析器可以處理的任何專案。 在函式傳回之後，批註的效果只適用于函式成功時。 這個範例會示範 `_Success_` 如何與 `_Out_` 互動，以執行正確的動作。 您可以使用關鍵字 `return` 來代表傳回值。  
  
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
  
 `_Out_` 批註會導致 Visual Studio Code 分析，以驗證呼叫端是否將非 Null 指標傳遞給 `pInt`的緩衝區，並在傳回之前由函式初始化緩衝區。  
  
## <a name="sal-best-practice"></a>SAL 最佳做法  
  
### <a name="adding-annotations-to-existing-code"></a>將注釋加入至現有程式碼  
 SAL 是一項功能強大的技術，可協助您改善程式碼的安全性和可靠性。 在您學習 SAL 之後，就可以將新技能套用到您的每日工作。 在新程式碼中，您可以在整個設計中使用 SAL 架構的規格。在較舊的程式碼中，您可以累加地新增批註，並藉此增加每次更新時的權益。  
  
 Microsoft 公用標頭已標注。 因此，建議您在專案中先標注分葉節點函式和函式，這些函式會呼叫 Win32 Api 以取得最大效益。  
  
### <a name="when-do-i-annotate"></a>我何時標注？  
 以下是一些指導方針：  
  
- 標注所有指標參數。  
  
- 標注值範圍的注釋，讓程式碼分析可以確保緩衝區和指標的安全。  
  
- 標注鎖定規則和鎖定副作用。 如需詳細資訊，請參閱[標注鎖定行為](../code-quality/annotating-locking-behavior.md)。  
  
- 標注驅動程式屬性和其他特定網域的屬性。  
  
  或者您可以為所有參數加上批註，讓您的意圖清楚明瞭，讓您可以輕鬆地檢查批註是否已經完成。  
  
## <a name="related-resources"></a>相關資源  
 [程式碼分析小組 Blog](https://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/C++程式碼](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)缺失   
 [標注函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [批註](../code-quality/annotating-function-behavior.md)函式行為   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定批註套用的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
