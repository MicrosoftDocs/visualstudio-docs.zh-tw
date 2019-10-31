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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c67fb719c6ec87e7707a406e2e7f67cd71569b39
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189042"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager 物件

語言服務會執行程式碼視窗管理員，並負責管理裝飾（例如，下拉式列）。 如需詳細資訊，請參閱[使用舊版 API 自訂程式碼視窗](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)。

下表顯示 `VSCodeWindowManager` 物件中的介面。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|允許在程式碼視窗中加入或移除裝飾（例如下拉式橫條圖）。|