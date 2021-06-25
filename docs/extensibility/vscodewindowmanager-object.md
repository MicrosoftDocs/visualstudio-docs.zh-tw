---
title: VSCodeWindowManager 物件 |Microsoft Docs
description: 深入瞭解 VSCodeWindowManager 物件，此物件負責管理裝飾，例如下拉式清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 76ab3d2a72c957b20a79850dc312f5c16de98afc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905289"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager 物件

語言服務會執行程式碼視窗管理員，負責管理裝飾 (例如，下拉式列) 。 如需詳細資訊，請參閱 [使用舊版 API 自訂程式碼視窗](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)。

下表顯示物件中的介面 `VSCodeWindowManager` 。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|允許在程式碼視窗中加入或移除裝飾 (例如下拉式橫條圖) 。|