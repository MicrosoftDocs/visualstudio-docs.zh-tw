---
title: VSCode視窗管理員物件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17bc9462af55ec9621654bd39cd65a2091f3f73f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740413"
---
# <a name="vscodewindowmanager-object"></a>VSCode 視窗管理員物件

語言服務實現代碼視窗管理器,並負責管理修飾(例如,下拉欄)。 關於詳細資訊,請參閱[使用舊 API 自訂代碼視窗](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)。

下表顯示了物件中的`VSCodeWindowManager`介面。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|允許將修飾(如下拉欄)添加到代碼視窗或從代碼視窗中刪除。|
