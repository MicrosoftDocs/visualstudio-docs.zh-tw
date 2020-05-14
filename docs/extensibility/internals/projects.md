---
title: 專案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706206"
---
# <a name="projects"></a>專案
在 Visual Studio 中,專案是開發人員用來組織原始程式碼檔以及**解決方案資源管理器**中顯示的其他資源的容器。 通常,專案是檔(例如,C# 專案的 .csproj 檔),用於存儲對原始程式碼檔和資源(如位圖檔)的引用。 項目允許您組織、構建、除錯和部署原始碼、對 Web 服務和資料庫的引用以及其他資源。 VS 套件可以透過三種主要式延伸 Visual Studio 專案系統:*專案類型*,*專案子型態*與*自訂工具*。

## <a name="in-this-section"></a>本節內容
- [專案類型](../../extensibility/internals/project-types.md)

 *項目類型*增加了對新類型的專案(如程式設計語言)的支援。 例如,Visual Studio 支援的每種語言都有自己的項目類型,IronPython 集成範例包括 IronPython 語言的項目類型。 您必須為 C# 或 Visual Basic 以外的語言建立專案類型,以自訂**如何在解決方案資源管理器**中生成、調試、部署和顯示專案。 有關詳細資訊,請參閱[項目類型](../../extensibility/internals/project-types.md)。

- [專案子類型](../../extensibility/internals/project-subtypes.md)

 *專案子類型*基於項目類型,可用於自定義專案的生成、調試和部署方式。 Visual Studio 使用智慧設備專案的專案子類型;他們通過將新構建的程式從開發計算機複製到目標設備來自定義部署。 C# 和可視化基本項目類型可用作專案子類型的基礎;C++專案類型不能。 您自己的項目類型也可以用作專案子類型的基礎。 有關詳細資訊,請參閱[項目子類型](../../extensibility/internals/project-subtypes.md)。

- [Web 專案](../../extensibility/internals/web-projects.md)

 解釋 Web 專案,而 Web 專案又創建 Web 應用程式。

- [新專案生成:引擎蓋下,第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)和[新專案生成:在引擎蓋下,第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 說明創建新項目時實際發生的情況。

- [VSSDK 樣本](https://github.com/Microsoft/VSSDK-Extensibility-Samples)包含 VSSDK 中處理專案和解決方案的範例。

## <a name="related-sections"></a>相關章節
- [深入探索 Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 解釋可視化工作室擴展性的不同方面。
