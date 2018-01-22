---
title: "C/c + + 判斷提示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
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
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a53c03f1ab2c8680329f17bfa36a49b12062bff5
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="cc-assertions"></a>C/C++ 判斷提示
判斷提示陳述式會指定您希望為您程式中的點，則為 true 的條件。 如果該條件不成立，判斷提示會失敗，中斷程式執行，而[判斷提示失敗對話方塊](../debugger/assertion-failed-dialog-box.md)隨即出現。  
  
 Visual c + + 支援下列建構函式為基礎的判斷提示陳述式：  
  
-   MFC 程式的 MFC 判斷提示。  
  
-   [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert)使用 ATL 的程式  
  
-   使用 C 執行階段程式庫的程式的 CRT 判斷提示。  
  
-   ANSI [assert 函式](/cpp/c-runtime-library/reference/assert-macro-assert-wassert)其他 C/c + + 程式。  
  
 您可以使用判斷提示來攔截邏輯錯誤、 檢查作業的結果和測試應該要處理的錯誤狀況。  
  
##  <a name="BKMK_In_this_topic"></a>本主題內容  
 [判斷提示的運作方式](#BKMK_How_assertions_work)  
  
 [偵錯和發行組建中的判斷提示](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [使用判斷提示的副作用](#BKMK_Side_effects_of_using_assertions)  
  
 [CRT 的判斷提示](#BKMK_CRT_assertions)  
  
 [MFC 判斷提示](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID 和 CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [AssertValid 的限制](#BKMK_Limitations_of_AssertValid)  
  
 [使用判斷提示](#BKMK_Using_assertions)  
  
-   [攔截邏輯錯誤](#BKMK_Catching_logic_errors)  
  
-   [檢查結果](#BKMK_Checking_results_)  
  
-   [正在尋找未處理的錯誤](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a>判斷提示的運作方式  
 當偵錯工具會中止，因為 MFC 或 C 執行階段程式庫判斷提示時，如果來源可供使用，偵錯工具巡覽發生判斷提示的來源檔案中的點。 判斷提示訊息會出現在[輸出 視窗](../ide/reference/output-window.md)和**判斷提示失敗** 對話方塊。 您可以將複製的判斷提示訊息**輸出**視窗文字視窗，如果您想要儲存供日後參考。 **輸出**視窗可能包含其他錯誤訊息。 這些訊息仔細地檢查，因為它們提供的判斷提示失敗原因的線索。  
  
 使用判斷提示來偵測在開發期間的錯誤。 一般而言，使用每個假設一個判斷提示。 比方說，如果您假設引數不是 NULL，若要測試這個假設使用判斷提示。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>偵錯和發行組建中的判斷提示  
 判斷提示陳述式編譯，只有當`_DEBUG`定義。 否則，編譯器會判斷提示視為 null 陳述式。 因此，判斷提示陳述式強制執行任何額外負荷，或效能成本在最終發行版本程式中，並可讓您避免使用`#ifdef`指示詞。  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a>使用判斷提示的副作用  
 當您加入判斷提示程式碼時，請確定判斷提示不會有副作用。 例如，請考慮下列判斷提示，以修改`nM`值：  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 因為`ASSERT`您程式中，發行版本中不會評估運算式`nM`將偵錯和發行版本中有不同的值。 若要避免這個問題，在 MFC 中的，您可以使用[確認](/cpp/mfc/reference/diagnostic-services#verify)巨集，而不是`ASSERT`。  `VERIFY`評估所有版本中的運算式，但不會檢查發行版本中的結果。  
  
 要特別小心在判斷提示陳述式中使用函式呼叫相關的因為評估函式可能會有未預期的副作用。  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`呼叫`myFnctn`在偵錯和發行版本中，因此是可接受的使用。 不過，使用`VERIFY`會加諸的發行版本中不必要的函式呼叫的額外負荷。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a>CRT 的判斷提示  
 CRTDBG。H 標頭檔會定義[_ASSERT 和 _ASSERTE 巨集](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)判斷提示檢查。  
  
|巨集|結果|  
|-----------|------------|  
|`_ASSERT`|如果指定的運算式評估為 FALSE，檔名和行號的`_ASSERT`。|`_ASSERTE`|  
|`_ASSERTE`|與相同`_ASSERT`，再加上已判斷提示的運算式的字串表示。|  
  
 `_ASSERTE`因為它會報告已判斷提示的運算式已是 FALSE，則是更為強大。 這可能足夠找出問題，而不會參考的原始程式碼。 不過，您的應用程式的偵錯版本會包含使用每個運算式的字串常數`_ASSERTE`。 如果您使用多個`_ASSERTE`巨集，這些字串的運算式會佔用大量的記憶體。 如果就證明有問題，使用`_ASSERT`以節省記憶體。  
  
 當`_DEBUG`定義，`_ASSERTE`巨集的定義如下：  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 如果已判斷提示的運算式評估為 FALSE， [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)呼叫以報告 （依預設使用的訊息對話方塊） 判斷提示失敗。 如果您選擇**重試**在 [訊息] 對話方塊`_CrtDbgReport`傳回 1 和`_CrtDbgBreak`透過偵錯工具會呼叫`DebugBreak`。  
  
### <a name="checking-for-heap-corruption"></a>檢查堆積損毀  
 下列範例會使用[_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)檢查堆積損毀：  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### <a name="checking-pointer-validity"></a>檢查指標有效性  
 下列範例會使用[_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer)來驗證指定的記憶體範圍是否有效進行讀取或寫入。  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 下列範例會使用[_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer)驗證指標會指向本機堆積中記憶體 (在堆積所建立和管理這個執行個體的 C 執行階段程式庫 — DLL 可以有自己的程式庫中，執行個體和因此其專屬堆積，外部應用程式堆積）。 這個判斷提示會攔截不只 null 或超出範圍的位址，但也的靜態變數、 堆疊變數和任何其他非本機記憶體的指標。  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### <a name="checking-a-memory-block"></a>檢查記憶體區塊  
 下列範例會使用[_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock)以確認記憶體區塊會在本機堆積中，且具有有效的區塊型別。  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a>MFC 判斷提示  
 MFC 定義[ASSERT](http://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)巨集判斷提示檢查。 它也會定義`MFC ASSERT_VALID`和`CObject::AssertValid`方法來檢查的內部狀態`CObject`-衍生物件。  
  
 如果引數的 MFC`ASSERT`巨集判斷值為零或為 false，巨集中止程式執行並提醒使用者; 否則會繼續執行。  
  
 當判斷提示失敗時，訊息對話方塊顯示的原始程式檔和行號判斷提示的名稱。 如果您在對話方塊中選擇 [重試] 方塊中，呼叫[AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak)會偵錯工具中斷執行。 此時，您可以檢查呼叫堆疊和使用其他偵錯工具設施，來判斷 判斷提示失敗的原因。 如果您已啟用[恰好在時間偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)，而且已經沒有執行偵錯工具，對話方塊可以啟動偵錯工具。  
  
 下列範例示範如何使用`ASSERT`檢查函式的傳回值：  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 您可以使用判斷提示與[IsKindOf](/cpp/mfc/reference/cobject-class.md#CObject__IsKindOf)提供類型檢查函式引數的函式：  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 `ASSERT`巨集產生的發行版本中沒有程式碼。 如果您要評估的運算式中的發行版本，請使用[確認](/cpp/mfc/reference/diagnostic-services#verify)取代 ASSERT 巨集。  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID 和 CObject::AssertValid  
 [CObject::AssertValid](/cpp/mfc/reference/cobject-class.md#CObject__AssertValid)方法可讓您提供執行階段檢查的內部狀態的物件。 雖然您不需要覆寫`AssertValid`當您衍生您的類別，從`CObject`，您可以讓您的類別更可靠執行此動作。 `AssertValid`應該在所有物件的成員變數，以確認其包含有效的值上都執行判斷提示。 例如，它應該檢查指標成員變數不是 NULL。  
  
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
  
 當您覆寫`AssertValid`，呼叫的基底類別版本`AssertValid`執行您自己檢查之前。 然後使用 ASSERT 巨集檢查衍生類別中，唯一的成員如下所示：  
  
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
  
 例如，假設有一個類別`CMyData`，哪些商店[CObList](/cpp/mfc/reference/coblist-class)其中一個它的成員變數中。 `CObList`變數`m_DataList`，儲存的集合`CPerson`物件。 縮寫的宣告`CMyData`看起來像這樣：  
  
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
  
 `AssertValid`中覆寫`CMyData`看起來像這樣：  
  
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
  
 `CMyData`使用`AssertValid`機制來測試儲存在其資料成員的物件的有效性。 覆寫`AssertValid`的`CMyData`叫用`ASSERT_VALID`自己 m_pDataList 成員變數的巨集。  
  
 有效性測試不會停止此層級因為類別`CObList`也會覆寫`AssertValid`。 此覆寫執行額外的有效性測試清單的內部狀態。 因此，有效測試上`CMyData`物件會導致預存的內部狀態的額外的有效性測試`CObList`清單物件。  
  
 透過一些工作，您可以加入的有效性測試`CPerson`也儲存在清單中的物件。 您無法衍生類別`CPersonList`從`CObList`並覆寫`AssertValid`。 在覆寫時，您會呼叫`CObject::AssertValid`，然後逐一查看清單中，呼叫`AssertValid`每`CPerson`儲存在清單中的物件。 `CPerson`開頭本主題的已顯示的類別會覆寫`AssertValid`。  
  
 當您建置偵錯時，這是功能強大的機制。 當您後續建置發行版本時，此機制會自動關閉。  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a>AssertValid 的限制  
 觸發判斷提示會指出物件是絕對不正確，且會停止執行。 不過，缺乏判斷提示只會指出找不到任何問題，但物件不保證能夠良好。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a>使用判斷提示  
  
###  <a name="BKMK_Catching_logic_errors"></a>攔截邏輯錯誤  
 您可以設定判斷提示，必須根據您的程式邏輯，則為 true 的條件。 判斷提示會有任何作用，除非發生邏輯錯誤。  
  
 例如，假設您所模擬天然氣分子中容器和變數`numMols`代表分子總數。 這個數字不能小於零，因此您可能會包含 MFC 判斷提示陳述式如下：  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 或者，您可能會包含如下的 CRT 判斷提示：  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 如果您的程式正常運作，這些陳述式會執行任何動作。 如果邏輯錯誤會造成`numMols`小於零，不過，判斷提示會停止程式執行，並顯示[判斷提示失敗對話方塊](../debugger/assertion-failed-dialog-box.md)。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a>檢查結果  
 判斷提示是用來測試其結果不明顯的快速視覺檢視作業的價值。  
  
 例如，請考慮下列程式碼會更新變數`iMols`指向連結清單的內容為基礎`mols`:  
  
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
  
 根據計算分子數目`iMols`永遠必須小於或等於分子，總數`numMols`。 迴圈的視覺檢視不會顯示，這一定會有大小寫，因此判斷提示陳述式在迴圈之後使用該條件的測試。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a>正在尋找未處理的錯誤  
 您可以使用判斷提示程式碼中測試錯誤條件，在時間點也就是其中的任何錯誤應該已處理。 在下列範例中，圖形常式會傳回錯誤碼或成功的零。  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 錯誤的錯誤處理程式碼正常運作，如果應該處理和`myErr`重設為零達到判斷提示之前。 如果`myErr`有另一個值，判斷提示失敗，程式會中止和[判斷提示失敗對話方塊](../debugger/assertion-failed-dialog-box.md)隨即出現。  
  
 判斷提示陳述式不是替代錯誤處理程式碼，但是。 下列範例顯示可能會造成問題，在最後發行版本程式碼中的判斷提示陳述式：  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 此程式碼依賴判斷提示陳述式來處理錯誤狀況。 如此一來，任何傳回錯誤碼`myGraphRoutine`將無法處理的最後發行版本程式碼中。  
  
 [本主題內容](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)