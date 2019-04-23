---
title: C-C++判斷提示 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759376a6682287cbe41d4d1dc13666c5a540f8e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050553"
---
# <a name="cc-assertions"></a>C/C++ 判斷提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

判斷提示陳述式會指定您預期要在程式中的某一點，則為 true 的條件。 如果該條件不成立，判斷提示失敗，將會中斷程式執行，而[判斷提示失敗對話方塊](../debugger/assertion-failed-dialog-box.md)隨即出現。  

 視覺化C++支援下列建構為基礎的判斷提示陳述式：  

- MFC 程式的 MFC 判斷提示。  

- [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3)使用 ATL 的程式  

- 使用 C 執行階段程式庫的程式的 CRT 判斷提示。  

- ANSI [assert 函式](http://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40)適用於其他 C /C++程式。  

  若要攔截邏輯錯誤，檢查作業的結果及測試應該已處理的錯誤狀況，您可以使用判斷提示。  

## <a name="BKMK_In_this_topic"></a>本主題內容  
 [判斷提示的運作方式](#BKMK_How_assertions_work)  

 [在偵錯和發行組建中的判斷提示](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [使用判斷提示的副作用](#BKMK_Side_effects_of_using_assertions)  

 [CRT 的判斷提示](#BKMK_CRT_assertions)  

 [MFC 判斷提示](#BKMK_MFC_assertions)  

- [MFC ASSERT_VALID 和 CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [AssertValid 的限制](#BKMK_Limitations_of_AssertValid)  

  [使用判斷提示](#BKMK_Using_assertions)  

- [攔截邏輯錯誤](#BKMK_Catching_logic_errors)  

- [檢查結果](#BKMK_Checking_results_)  

- [找出未處理的錯誤](#BKMK_Testing_error_conditions_)  

## <a name="BKMK_How_assertions_work"></a> 判斷提示的運作方式  
 當偵錯工具暫止因為 MFC 或 C 執行階段程式庫判斷提示時，則來源是否可用，偵錯工具導覽到判斷提示的發生位置的原始程式檔中的點。 判斷提示訊息會出現在[輸出視窗](../ide/reference/output-window.md)並**判斷提示失敗** 對話方塊。 您可以將複製的判斷提示訊息**輸出**視窗文字視窗，如果您想要儲存起來供日後參考。 **輸出**視窗可能會包含其他錯誤訊息。 仔細檢查這些訊息，因為它們提供的判斷提示失敗原因的線索。  

 使用判斷提示來偵測在開發期間的錯誤。 因此，使用每個假設一個判斷提示。 比方說，如果您假設引數不是 NULL，請使用判斷提示來測試這個假設。  

 [本主題內容](#BKMK_In_this_topic)  

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> 在偵錯和發行組建中的判斷提示  
 判斷提示陳述式編譯，只有當`_DEBUG`定義。 否則，編譯器會將判斷提示視為 null 陳述式中。 因此，判斷提示陳述式造成沒有的額外負荷或效能成本在最終發行程式中，並可讓您避免使用`#ifdef`指示詞。  

## <a name="BKMK_Side_effects_of_using_assertions"></a> 使用判斷提示的副作用  
 當您加入判斷提示程式碼時，請確定判斷提示並沒有副作用。 例如，請考慮下列判斷提示，以修改`nM`值：  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 因為`ASSERT`不會在您的程式的發行版本中評估運算式`nM`將偵錯和發行版本中有不同的值。 若要避免這個問題，在 MFC 中的，您可以使用[VERIFY](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)巨集，而不是`ASSERT`。  `VERIFY` 評估所有版本中的運算式，但不會檢查發行版本中的結果。  

 要特別小心使用判斷提示陳述式中的函式呼叫的相關，因為評估函式可以有未預期的副作用。  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` 呼叫`myFnctn`在偵錯和發行版本中，因此是可接受的使用。 不過，使用`VERIFY`加諸的發行版本中不必要的函式呼叫的額外負荷。  

 [本主題內容](#BKMK_In_this_topic)  

## <a name="BKMK_CRT_assertions"></a> CRT 的判斷提示  
 CRTDBG。H 標頭檔會定義[_ASSERT 和 _ASSERTE 巨集](http://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36)判斷提示檢查。  

|   巨集    |                                             結果                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | 如果指定的運算式評估為 FALSE，檔案名稱和行號的`_ASSERT`。 |
| `_ASSERTE` |      與相同`_ASSERT`，再加上已判斷提示的運算式的字串表示。       |

 `_ASSERTE` 因為它會報告已判斷提示的運算式，原來是 FALSE，則會是更強大。 這可能不足以找出問題，而不會參考的原始程式碼。 不過，您的應用程式的偵錯版本會包含每個運算式使用的字串常數`_ASSERTE`。 如果您使用多個`_ASSERTE`巨集，這些字串運算式佔用大量的記憶體。 如果這證實有問題，使用`_ASSERT`為了節省記憶體。  

 當`_DEBUG`定義，`_ASSERTE`巨集定義，如下所示：  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 如果判斷提示的運算式評估為 FALSE 時， [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)呼叫以報告 （依預設使用訊息對話方塊） 判斷提示失敗。 如果您選擇**重試**[訊息] 對話方塊中，在`_CrtDbgReport`會傳回 1 和`_CrtDbgBreak`呼叫偵錯工具，透過`DebugBreak`。  

### <a name="checking-for-heap-corruption"></a>檢查堆積損毀  
 下列範例會使用[_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765)檢查堆積損毀：  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>檢查指標有效性  
 下列範例會使用[_CrtIsValidPointer](http://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa)來檢查指定的記憶體範圍是否有效用於讀取或寫入。  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 下列範例會使用[_CrtIsValidHeapPointer](http://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5)驗證指標會指向本機堆積中的記憶體 (堆積所建立和管理這個執行個體的 C 執行階段程式庫 — DLL 可以有自己的執行個體的程式庫，以及因此其專屬堆積，外部應用程式堆積）。 這個判斷提示會攔截不只為 null 或超出範圍的位址，但也要靜態變數、 堆疊變數和任何其他非本機記憶體的指標。  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>檢查記憶體區塊  
 下列範例會使用[_CrtIsMemoryBlock](http://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273)以確認記憶體區塊位於本機堆積，且具有有效的區塊類型。  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [本主題內容](#BKMK_In_this_topic)  

## <a name="BKMK_MFC_assertions"></a> MFC 判斷提示  
 定義 MFC [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)巨集來判斷提示檢查。 它也會定義`MFC ASSERT_VALID`並`CObject::AssertValid`方法來檢查的內部狀態`CObject`-衍生物件。  

 如果引數的 MFC`ASSERT`巨集判斷值為零或為 false，巨集終止程式執行並警告使用者; 否則會繼續執行。  

 當判斷提示失敗時，[訊息] 對話方塊中顯示的原始程式檔和行號的判斷提示的名稱。 如果您在對話方塊中選擇 [重試] 方塊中，呼叫[AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30)會中斷偵錯工具執行。 此時，您可以檢查呼叫堆疊，並使用其他偵錯工具設施判斷判斷提示失敗的原因。 如果您已啟用[時間只要偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)，偵錯工具已不在執行，對話方塊可以啟動偵錯工具。  

 下列範例示範如何使用`ASSERT`檢查函式的傳回值：  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 您可以使用與判斷提示[IsKindOf](http://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6)提供類型檢查函數的引數的函式：  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 `ASSERT`巨集產生的發行版本中的任何程式碼。 如果您要評估的運算式中的發行版本，請使用[確認](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)取代 ASSERT 巨集。  

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID 和 CObject::AssertValid  
 [CObject::AssertValid](http://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157)方法可讓您提供執行階段檢查物件的內部狀態。 雖然您不需要覆寫`AssertValid`當您衍生您的類別，從`CObject`，您可以讓您的類別更可靠的執行此動作。 `AssertValid` 應該在所有物件的成員變數，以確認它們包含有效的值上都執行判斷提示。 比方說，它應該檢查指標成員變數不是 NULL。  

 下列範例示範如何宣告`AssertValid`函式：  

```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  

```  

 當您覆寫`AssertValid`，呼叫的基底類別版本`AssertValid`才能執行您自己的檢查。 然後使用 ASSERT 巨集檢查衍生類別中，唯一的成員如下所示：  

```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  

    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  

```  

 如果任何成員變數儲存物件時，您可以使用`ASSERT_VALID`巨集來測試其內部有效性 (如果它們的類別覆寫`AssertValid`)。  

 例如，假設類別`CMyData`，哪些存放區[CObList](http://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca)其中一種其成員變數。 `CObList`變數`m_DataList`，會儲存一組`CPerson`物件。 縮寫的 deklarace`CMyData`看起來像這樣：  

```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  

```  

 `AssertValid`覆寫中`CMyData`看起來像這樣：  

```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  

```  

 `CMyData` 使用`AssertValid`機制，以測試其資料成員中儲存的物件是否有效。 覆寫`AssertValid`的`CMyData`叫用`ASSERT_VALID`自己 m_pDataList 成員變數的巨集。  

 有效性測試不會停止在此層級因為類別`CObList`也會覆寫`AssertValid`。 此覆寫會執行額外的有效性測試清單的內部狀態。 因此，在上進行測試有效性`CMyData`物件會導致額外的有效性測試預存的內部狀態`CObList`清單物件。  

 透過一些工作，您可以新增有效性測試`CPerson`也儲存在清單中的物件。 您可以衍生類別`CPersonList`從`CObList`，並覆寫`AssertValid`。 在覆寫時，您會呼叫`CObject::AssertValid`，然後逐一查看清單中，呼叫`AssertValid`每個`CPerson`儲存在清單中的物件。 `CPerson`本主題開頭的已顯示的類別會覆寫`AssertValid`。  

 當您建置適用於偵錯時，這是功能強大的機制。 當您後續建置版本時，機制會自動關閉。  

### <a name="BKMK_Limitations_of_AssertValid"></a> AssertValid 的限制  
 觸發判斷提示會指出物件一定是壞，且會停止執行。 不過，缺乏判斷提示表示只找不到任何問題，但物件不保證為良好。  

 [本主題內容](#BKMK_In_this_topic)  

## <a name="BKMK_Using_assertions"></a> 使用判斷提示  

### <a name="BKMK_Catching_logic_errors"></a> 攔截邏輯錯誤  
 您可以設定判斷提示的條件，必須根據您的程式邏輯，則為 true。 判斷提示會有任何作用，除非發生邏輯錯誤。  

 例如，假設您在模擬中容器和變數的天然氣微觀`numMols`代表微觀總數。 這個數字不能小於零，因此您可能會包含如下的 MFC 判斷提示陳述式：  

```  
ASSERT(numMols >= 0);  

```  

 或者，您可能會包含如下的 CRT 判斷提示：  

```  
_ASSERT(numMols >= 0);  
```  

 如果您的程式正常運作，這些陳述式會執行任何動作。 如果邏輯錯誤會造成`numMols`小於零，不過，判斷提示暫止程式執行並顯示[判斷提示失敗對話方塊](../debugger/assertion-failed-dialog-box.md)。  

 [本主題內容](#BKMK_In_this_topic)  

### <a name="BKMK_Checking_results_"></a> 檢查結果  
 判斷提示是重要的測試的作業的結果並不明顯的快速視覺檢查。  

 例如，請考慮下列的程式碼，以更新變數`iMols`所指向的連結清單的內容為基礎`mols`:  

```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  

 大部分的數目來計算`iMols`永遠必須小於或等於微觀，總數`numMols`。 迴圈的視覺檢查不會顯示，這一定會在案例中，所以判斷提示陳述式會使用迴圈後，該條件的測試。  

 [本主題內容](#BKMK_In_this_topic)  

### <a name="BKMK_Testing_error_conditions_"></a> 找出未處理的錯誤  
 您可以使用判斷提示程式碼中，測試錯誤條件的某一點也就是其中的任何錯誤應該已處理。 在下列範例中，圖形的常式會傳回錯誤碼或零，代表成功。  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 如果錯誤處理程式碼正常運作，應該處理錯誤和`myErr`重設為零的判斷提示達到之前。 如果`myErr`有另一個值，判斷提示失敗，則程式會中止，而[判斷提示失敗對話方塊](../debugger/assertion-failed-dialog-box.md)隨即出現。  

 判斷提示陳述式不能替代錯誤處理程式碼，不過。 下列範例顯示可能會導致問題的最終發行程式碼中的判斷提示陳述式：  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 此程式碼依賴處理錯誤狀況的判斷提示陳述式。 如此一來，任何錯誤碼傳回`myGraphRoutine`將無法處理的最終發行程式碼中。  

 [本主題內容](#BKMK_In_this_topic)  

## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)
