---
title: IDispatchEx::GetNextDispID | Microsoft Docs
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
ms.openlocfilehash: 4d964a8744f1f0a28704dd0a1d5e0fd2e67aab1c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58897669"
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
決定要列舉的一組項目。 這可以是下列值的組合：

|值|意義|
|-----------|-------------|
|fdexEnumDefault|要求物件列舉的預設項目。 物件可以列舉任何一組的項目。|
|fdexEnumAll|要求物件列舉的所有項目。 物件可以列舉任何一組的項目。|

`id`\
識別目前的成員。 GetNextDispID 擷取後此列舉型別中的項目。 若要取得這個識別項，會使用 GetDispID 或 GetNextDispID 之前呼叫。 若要取得第一個項目的第一個識別項使用 DISPID_STARTENUM 值。

`pid`\
列舉中接收的下一個項目識別項的 DISPID 變數的位址。

如果成員已遭刪除`DeleteMemberByName`或是`DeleteMemberByDispID`，則`DISPID`要保持有效`GetNextDispID`。

## <a name="return-value"></a>傳回值

會傳回下列值之一：

|||
|-|-|
|`S_OK`|成功。|
|`S_FALSE`|是列舉型別。|

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