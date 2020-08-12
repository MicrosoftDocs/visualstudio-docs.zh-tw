---
title: IDispatchEx：： GetNextDispID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144425"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

列舉物件的成員。

## <a name="syntax"></a>語法

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>參數

`grfdex`\
決定要列舉的專案集合。 這可以是下列值的組合：

|值|意義|
|-----------|-------------|
|fdexEnumDefault|要求物件列舉預設元素。 允許物件列舉任何一組元素。|
|fdexEnumAll|要求物件列舉所有元素。 允許物件列舉任何一組元素。|

`id`\
識別目前的成員。 GetNextDispID 會抓取列舉中的專案。 會使用 GetDispID 或先前的 GetNextDispID 呼叫來取得此識別碼。 會使用 DISPID_STARTENUM 值來取得第一個專案的第一個識別碼。

`pid`\
DISPID 變數的位址，可接收列舉中下一個專案的識別碼。

如果或刪除了成員 `DeleteMemberByName` `DeleteMemberByDispID` ，則 `DISPID` 必須保持對的有效 `GetNextDispID` 。

## <a name="return-value"></a>傳回值

傳回下列其中一值：

|值|意義|
|-|-|
|`S_OK`|成功。|
|`S_FALSE`|列舉已完成。|

## <a name="example"></a>範例

```cpp
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

- [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)