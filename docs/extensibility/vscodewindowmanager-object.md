---
title: VSCodeWindowManager 物件 |Microsoft Docs
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
ms.openlocfilehash: 9668336c565b4a3be332509d1c960b067a486785
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583628"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager 物件

語言服務會執行程式碼視窗管理員，負責管理裝飾 (例如，下拉式列) 。 如需詳細資訊，請參閱 [使用舊版 API 自訂程式碼視窗](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true)。

下表顯示物件中的介面 `VSCodeWindowManager` 。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|允許在程式碼視窗中加入或移除裝飾 (例如下拉式橫條圖) 。|