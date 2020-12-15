---
title: VSPackage 結構 (原始檔控制 VSPackage) |Microsoft Docs
description: 深入瞭解原始檔控制封裝 SDK，此 SDK 提供 VSPackage 與原始檔控制實施者整合，以與 Visual Studio 整合的指導方針。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5850dfb2448364124c8f1778eac48ac9c653269
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487955"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 結構 (原始檔控制 VSPackage)

原始檔控制封裝 SDK 提供建立 VSPackage 的指導方針，可讓原始檔控制實施者將其原始檔控制功能與 Visual Studio 環境整合。 VSPackage 是一種 COM 元件，Visual Studio 整合式開發環境 (IDE) 根據封裝在登錄專案中通告的服務，視需要載入。 每個 VSPackage 都必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 。 VSPackage 通常會取用 Visual Studio IDE 所提供的服務，並這個本身的一些服務。

VSPackage 會宣告其功能表項目，並透過 .vsct 檔案建立預設專案狀態。 Visual Studio IDE 會顯示此狀態下的功能表項目，直到載入 VSPackage 為止。 接著，會呼叫方法的 VSPackage 執行， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 以啟用或停用功能表項目。

## <a name="source-control-package-characteristics"></a>原始檔控制封裝特性

原始檔控制 VSPackage 已緊密整合至 Visual Studio。 VSPackage 語義包括：

- 藉由 VSPackage 介面 (介面所執行的介面 `IVsPackage`) 

- UI 命令執行 ( .vsct 檔案和介面的執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 

- 使用 Visual Studio 註冊 VSPackage。

原始檔控制 VSPackage 必須與這些 Visual Studio 實體通訊：

- 專案

- 編輯器

- 方案

- Windows

- 執行中的檔資料表

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>可能耗用的 Visual Studio 環境服務

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider 服務

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>執行並呼叫 VSIP 介面

原始檔控制封裝是一種 VSPackage，因此可以直接與向 Visual Studio 註冊的其他 Vspackage 互動。 為了提供原始檔控制功能的完整廣度，原始檔控制 VSPackage 可以處理專案或 shell 所提供的介面。

Visual Studio 中的每個專案都必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> ，才能在 VISUAL STUDIO IDE 中被辨識為專案。 不過，這個介面並非專門用於原始檔控制。 預期會在原始檔控制下執行的專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 。 原始檔控制 VSPackage 會使用此介面來查詢專案的內容，並提供它的圖像和系結資訊 (所需的資訊，以建立伺服器位置與原始檔控制) 之專案的磁片位置之間的連接。

原始檔控制 VSPackage 會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> ，進而允許專案自行註冊原始檔控制，並取得其狀態圖像。

如需原始檔控制 VSPackage 必須考慮的介面完整清單，請參閱 [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。

## <a name="see-also"></a>另請參閱

- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
