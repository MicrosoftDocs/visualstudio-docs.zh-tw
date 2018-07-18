---
title: VSPackage 結構 (原始檔控制 VSPackage) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d36e31db9c47325e62fe759cd5030c5f24fb73be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057614"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 結構 (原始檔控制 VSPackage)

原始檔控制封裝 SDK 會提供建立 VSPackage 的指導方針可讓原始檔控制實作者，他或她的原始檔控制功能整合在 Visual Studio 環境。 VSPackage 是通常視需要載入由 Visual Studio 整合式的開發環境 (IDE) 會由其登錄項目中的封裝公告服務為基礎的 COM 元件。 每個 VSPackage 必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 通常會使用 Visual Studio IDE 所提供的服務，並提供其本身的某些服務。

VSPackage 會宣告其功能表項目，並建立透過.vsct 檔的預設項目狀態。 Visual Studio IDE 會顯示功能表項目處於此狀態，直到載入 VSPackage。 接著，VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼叫方法來啟用或停用功能表項目。

## <a name="source-control-package-characteristics"></a>原始檔控制封裝特性

原始檔控制 VSPackage 已完全整合至 Visual Studio 中。 VSPackage 語意包括：

-   因為 VSPackage 實作介面 (`IVsPackage`介面)

-   UI 命令實作 (.vsct 檔並實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面)

-   使用 Visual Studio VSPackage 的註冊。

原始檔控制 VSPackage 這些其他的 Visual Studio 實體必須與通訊：

-   專案

-   編輯器

-   方案

-   Windows

-   執行中的文件表格

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio 環境服務使用

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider 服務

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP 介面實作，並呼叫

原始檔控制套件的 VSPackage，且因此可直接與其他已向 Visual Studio 的 Vspackage 中互動。 為了提供原始檔控制功能的完整範圍，原始檔控制 VSPackage 可以處理專案或殼層所提供的介面。

在 Visual Studio 中的每個專案必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>視為 Visual Studio IDE 中的專案。 不過，此介面不特製化足夠用於原始檔控制。 應該是來源底下的專案控制實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 這個介面是由原始檔控制 VSPackage 來查詢其內容的專案，並提供它圖像 （glyph） 和繫結資訊 （所需的資訊來建立的伺服器位置與專案下的磁碟位置之間的連線原始檔控制）。

原始檔控制 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，這可讓專案以註冊其本身的原始檔控制，並擷取其狀態的圖像 （glyph）。

原始檔控制 VSPackage 必須考量的介面的完整清單，請參閱 <<c0> [ 相關的服務與介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。

## <a name="see-also"></a>另請參閱

- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)