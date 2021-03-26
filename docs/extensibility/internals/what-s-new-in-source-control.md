---
title: Visual Studio 2015 SDK 中原始檔控制的新功能 |Microsoft Docs
description: 瞭解原始檔控制 Vspackage 的功能，並查看執行步驟的總覽。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da10750629fcdae66ab8456b3074c07f44e3cf05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069058"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK 原始檔控制的新功能

在中 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ，您可以藉由執行原始檔控制 VSPackage，提供更緊密整合的原始檔控制解決方案。 本節說明原始檔控制 Vspackage 的功能，並提供執行步驟的總覽。

## <a name="the-source-control-vspackage"></a>原始檔控制 VSPackage

Visual Studio 支援兩種類型的原始檔控制解決方案。 在所有版本的 Visual Studio 中，您仍然可以整合原始檔控制外掛程式 API 型外掛程式。 您也可以建立原始檔控制的 VSPackage，以提供 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 適用于原始檔控制解決方案的深層整合路徑，而這些解決方案需要高層級的複雜和自主性。

VSPackage 可將幾乎任何一種功能新增至 Visual Studio。 原始檔控制 VSPackage 提供 Visual Studio 的完整原始檔控制功能，從向使用者呈現的 UI 到與原始檔控制系統的後端通訊。

執行原始檔控制 VSPackage 需要「全部」或「無」策略。 原始檔控制 VSPackage 的建立者必須投資大量的工作，以執行一些原始檔控制介面和新的 UI 元素， (對話方塊、功能表和工具列) 來涵蓋整個原始檔控制功能，以及任何封裝成功與 Visual Studio 整合所需的介面。

下列步驟提供執行原始檔控制封裝所需功能的一般總覽。 如需詳細資訊，請參閱 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。

1. 建立這個私用原始檔控制服務的 VSPackage。

2. 在 Visual Studio (所推出的原始檔控制相關服務中執行介面，例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> 介面) 。

3. 註冊您的原始檔控制 VSPackage。

4. 執行所有原始檔控制 UI，包括功能表項目、對話方塊、工具列和快顯功能表。

5. 所有原始檔控制相關事件都會傳遞至您的原始檔控制 VSackage （當其為使用中時），而且必須由您的 VSPackage 處理。

6. 您的原始檔控制 VSPackage 必須接聽事件（例如，執行介面的事件），以及 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 追蹤專案檔案 (TPD 由) 介面所執行的) 事件 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 並採取必要動作。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
