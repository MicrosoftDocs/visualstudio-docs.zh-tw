---
title: VS 包結構(來源控制 VS 套件) |微軟文件
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
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703813"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 結構 (原始檔控制 VSPackage)

源代碼管理包 SDK 提供了建立 VSPackage 的指南,該整合了原始碼管理實施者將其原始碼管理功能與 Visual Studio 環境整合。 VSPackage 是一個 COM 元件,通常由 Visual Studio 整合式開發環境 (IDE) 按需載入,該元件基於包在其註冊表條目中通告的服務。 每個 VS<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>套件 都必須實作 。 VSPackage 通常使用 Visual Studio IDE 提供的服務,並提供其自己的某些服務。

VSPackage 聲明其功能表項並透過 .vsct 檔案建立預設項狀態。 Visual Studio IDE 顯示處於此狀態的功能表項,直到載入 VSPackage。 隨後,VSPackage 的方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>的 實現被調用以啟用或禁用功能表項。

## <a name="source-control-package-characteristics"></a>原始碼管理套件功能

源代碼管理 VSPackage 深度集成到可視化工作室中。 VSPackage 語義包括:

- 透過 VSPackage(`IVsPackage`介面)實現介面

- UI 命令(.vsct 檔案與介面<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>)

- 在視覺工作室註冊 VS 包。

原始碼管理 VSPackage 必須與以下其他 Visual Studio 實體通訊:

- 專案

- 編輯器

- 方案

- Windows

- 執行的文件表

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>可能使用的視覺工作室環境服務

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SV註冊供應商服務

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>實作與呼叫的 VSIP 介面

原始程式碼管理套件是 VSPackage,因此可以直接與在 Visual Studio 註冊的其他 VSPackage 進行互動。 為了提供來源控制功能的全部範圍,原始程式碼管理 VSPackage 可以處理專案或 shell 提供的介面。

可視化工作室中的每個專案都必須實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>才能在可視化工作室 IDE 中識別為專案。 但是,此介面對於原始程式碼管理來說不夠專業。 預期受源碼管理的項目實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 原始碼管理 VSPackage 使用此介面查詢專案的內容,並為其提供字形和綁定資訊(在伺服器位置和受原始程式碼控制的專案的磁碟位置之間建立連接所需的資訊)。

原始碼管理 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>實現 ,這反過來又允許專案註冊自己進行原始程式碼管理並檢索其狀態字形。

有關原始碼管理 VSPackage 必須考慮的介面的完整清單,請參閱[相關服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。

## <a name="see-also"></a>另請參閱

- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [相關的服務和介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
