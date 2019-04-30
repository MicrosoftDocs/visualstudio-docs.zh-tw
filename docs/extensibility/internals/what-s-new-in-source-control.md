---
title: 在 Visual Studio 2015 SDK 中的原始檔控制中最新消息 |Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b667a6c6322a925b49290ab3234788a4eee3544
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856795"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>在 Visual Studio 2015 SDK 的原始檔控制中最新消息

在  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，您可以藉由實作原始檔控制 VSPackage 提供深入的整合式原始檔控制解決方案。 本節說明的原始檔控制 Vspackage 功能，並提供實作步驟的概觀。

## <a name="the-source-control-vspackage"></a>原始檔控制 VSPackage

Visual Studio 支援兩種類型的原始檔控制解決方案。 在所有版本的 Visual Studio 中，您仍舊可以以原始檔控制外掛程式 API 為基礎的外掛程式。 您也可以建立提供深入整合的原始檔控制 VSPackage[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]適用於原始檔控制解決方案需要高層級的複雜度與自我管理的路徑。

VSPackage 可以將幾乎所有種類的功能加入 Visual Studio。 原始檔控制 VSPackage 提供給使用者，以原始檔控制系統的後端通訊 UI 從 Visual Studio 中，完整的原始檔控制功能。

實作原始檔控制 VSPackage，需要 「 全部或全無 」 的策略。 原始檔控制 VSPackage 的建立者必須投入大量心力來實作許多原始檔控制的介面和新的 UI 項目 （對話方塊、 功能表和工具列） 以涵蓋整個原始檔控制功能，以及介面所需的任何套件已成功與 Visual Studio 整合。

下列步驟提供所需實作原始檔控制套件的一般概觀。 如需詳細資訊，請參閱 <<c0> [ 建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。

1. 建立提供私用的原始檔控制服務的 VSPackage。

2. 在原始檔控制相關服務，Visual Studio 會提供實作介面 (例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>介面)。

3. 註冊您的原始檔控制 VSPackage。

4. 實作所有的原始檔控制 UI，包括功能表項目、 對話方塊、 工具列和快顯功能表。

5. 所有的原始檔控制相關事件會傳遞至原始檔控制 VSackage 中，當它為作用中且必須由您的 VSPackage。

6. 原始檔控制 VSPackage 必須接聽事件，例如實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>介面及追蹤專案文件 (TPD) 事件 (由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面)，並採取必要動作。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)