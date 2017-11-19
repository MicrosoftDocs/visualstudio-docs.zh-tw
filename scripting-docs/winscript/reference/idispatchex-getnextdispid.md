---
title: "IDispatchEx::GetNextDispID |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
列舉物件的成員。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `grfdex`  
 決定要列舉的項目集。 這可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|fdexEnumDefault|要求物件列舉的預設項目。 允許物件列舉任何項目組。|  
|fdexEnumAll|要求物件列舉的所有項目。 允許物件列舉任何項目組。|  
  
 `id`  
 識別目前的成員。 GetNextDispID 擷取之後此列舉型別中的項目。 若要取得這個識別碼，會使用 GetDispID 或 GetNextDispID 先前呼叫。 若要取得第一個項目的第一個識別項使用 DISPID_STARTENUM 值。  
  
 `pid`  
 列舉中接收的下一個項目識別項的 DISPID 變數的位址。  
  
 如果成員已遭刪除`DeleteMemberByName`或`DeleteMemberByDispID`、`DISPID`必須一直保持有效`GetNextDispID`。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|已完成列舉。|  
  
## <a name="example"></a>範例  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)