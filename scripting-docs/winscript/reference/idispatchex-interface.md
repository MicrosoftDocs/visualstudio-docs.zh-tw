---
title: IDispatchEx 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22ccc54dee335fd8c81343557d2f32c48eb30560
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837915"
---
# <a name="idispatchex-interface"></a>IDispatchEx 介面
`IDispatchEx`延伸模組的`IDispatch`介面，適用於動態語言，例如指令碼語言的支援功能。 本章節描述`IDispatchEx`介面本身之間的差異`IDispatch`和`IDispatchEx`，延伸模組的原理。 預期讀者都熟悉`IDispatch`而且具有存取權`IDispatch`文件。  
  
## <a name="remarks"></a>備註  
 `IDispatch` 基本上被開發的 Microsoft Visual Basic。 主要限制`IDispatch`是，它就會假設物件都是靜態。 換句話說，因為執行階段期間不會變更物件，型別資訊可以完全描述其在編譯時期。 動態指令碼語言，例如 Visual Basic Scripting Edition (VBScript) 中找到的執行階段模型和[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]和物件模型，例如動態 HTML 需要更有彈性的介面。  
  
 `IDispatchEx` 開發提供的所有服務`IDispatch`以及適用於更動態的晚期繫結語言，例如指令碼語言的某些延伸模組。 其他功能`IDispatchEx`所提供不`IDispatch`是：  
  
- 將新成員加入至物件 ("expando")，使用`GetDispID`與`fdexNameEnsure`旗標。  
  
- 刪除物件的成員，使用`DeleteMemberByName`或`DeleteMemberByDispID`。  
  
- 區分大小寫的分派作業-使用`fdexNameCaseSensitive`或`fdexNameCaseInsensitive`。  
  
- 搜尋成員以隱含的名稱 — 使用`fdexNameImplicit`。  
  
- 列舉物件的 Dispid — 使用`GetNextDispID`。  
  
- 從 DISPID 的對應項目名稱 — 使用`GetMemberName`。  
  
- 取得物件成員的屬性 — 使用`GetMemberProperties`。  
  
- 含有方法引動過程`this`指標，使用`InvokeEx`使用，則為 DISPATCH_METHOD。  
  
- 允許瀏覽器支援的命名空間，以取得名稱空間物件之父系的概念 — 使用`GetNameSpaceParent`。  
  
  物件支援`IDispatchEx`也可能會支援`IDispatch`回溯相容性。 支援之物件的動態本質`IDispatchEx`有幾個含意`IDispatch`這些物件的介面。 比方說，`IDispatch`會進行下列假設：  
  
- 成員和參數 Dispid 必須保持不變的物件存留期。 這可讓用戶端取得 Dispid 次並快取它們，以供稍後使用。  
  
  因為`IDispatchEx`允許的新增和刪除成員，有效的 Dispid 的集合不會不保持不變。 不過，`IDispatchEx`需要 DISPID 和成員名稱之間的對應保持不變。 這表示，如果在刪除成員：  
  
- 建立具有相同名稱的成員之前，不能重複使用的 DISPID。  
  
- DISPID 必須保持有效`GetNextDispID`。  
  
- 必須依正常程序接受 DISPID，由任一`IDispatch`或`IDispatchEx`方法，它們必須辨識為已刪除的成員，並傳回適當的錯誤程式碼 （通常 DISP_E_MEMBERNOTFOUND 或 S_FALSE）。  
  
## <a name="examples"></a>範例  
 這[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]函式 test （） 中的程式碼會進行下列作業：  
  
- 建立新的物件，藉由呼叫`Object`建構函式並將指標指派給變數的 obj 之新物件  
  
- 建立新的項目之物件中名為 Elem 並指派給這個項目函式貓的指標。  
  
- 呼叫此函式。 因為它已呼叫方法，為`this`指標參考的物件 obj函式會將新的項目，列中的物件。  
  
  完整的 HTML 程式碼是：  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 放在這個相同的 Web 網頁上的控制項可以從瀏覽器，以取得對指令碼引擎分派指標。 控制項可以再實作函式 test （）：  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 從控制項的程式碼、 測試、 未與相同的工作[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]函式`test()`。 請注意，這些 dispatch 呼叫會結合成為執行[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎和引擎的狀態變更：  
  
- 取得 cat 函式使用分派指標`GetDispID()`。  
  
- 取得物件的函式使用分派指標`GetDispID()`。  
  
- 藉由呼叫物件在函數中的，會建構一個物件`InvokeEx()`和取得新建構的物件的分派指標。  
  
- 建立新的項目，Elem，在物件中使用`GetDispID()`與`fdexNameEnsure`旗標。  
  
- 將分派指標來在項目中使用 cat `InvokeEx()`。  
  
- 藉由呼叫，做為方法呼叫 cat 分派指標`InvokeEx()`和分派指標傳遞至建構的物件做為`this`指標。  
  
- Cat 方法會建立新的項目，在目前的列，`this`物件。  
  
- 確認新的項目，列中建構的物件，建立列舉的項目使用`GetNextDispID()`。  
  
  測試控制項的程式碼：  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>方法  
 [IDispatchEx 方法](../../winscript/reference/idispatchex-methods.md)