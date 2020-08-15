---
title: SCRIPTUICITEM 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75827d9ef38fdc18f87c231fbe9a909ebaaa120a
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238760"
---
# <a name="scriptuicitem-enumeration"></a>SCRIPTUICITEM 列舉
表示 UI 專案的類型。 用於 [IActiveScriptSiteUIControl：： GetUIBehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)中。  
  
## <a name="syntax"></a>語法  
  
```vb  
typedef enum tagSCRIPTUICITEM {     SCRIPTUICITEM_INPUTBOX = 1,     SCRIPTUICITEM_MSGBOX = 2,     } SCRIPTUICITEM;   
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|值|UI 專案類型|  
|-|-|  
|SCRIPTUICITEM_INPUTBOX|輸入控制項。|  
|SCRIPTUICITEM_MSGBOX|一個訊息方塊。|