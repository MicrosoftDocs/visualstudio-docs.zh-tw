---
title: 簡化嵌入 |Microsoft Docs
description: 瞭解簡化的內嵌，當其檔視圖物件是 Visual Studio 的子系時，可以在編輯器中啟用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dca3b0c11c916a1fc47e4687bfeeabee35bcdfb4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056372"
---
# <a name="simplified-embedding"></a>簡化嵌入
當編輯器的檔視圖物件是父代（ (也就是) 的子系 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，而 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面會實作為處理其視窗命令）時，就會在編輯器中啟用簡化嵌入。 簡化的內嵌編輯器無法裝載活動控制項。 下圖顯示用來建立具有簡化內嵌之編輯器的物件。

 ![簡化的內嵌編輯器圖形](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") 具有簡化內嵌的編輯器

> [!NOTE]
> 在此圖的物件中，只 `CYourEditorFactory` 需要物件才能建立標準檔案型編輯器。 如果您要建立自訂編輯器，則不需要執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ，因為您的編輯器可能會有自己的私用持續性機制。 但是針對非自訂編輯器，您必須這樣做。

 物件中包含的所有介面都是以簡化的內嵌來建立編輯器 `CYourEditorDocument` 。 不過，若要支援多個檔資料檢視，請將介面分割成不同的資料，並依下表所示的方式來查看物件。

|介面|介面的位置|使用|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|檢視|提供父視窗的連接。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|檢視|處理命令。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|檢視|啟用狀態列更新。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|檢視|啟用 **工具箱** 專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|資料|當檔案變更時傳送通知。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|資料|啟用檔案類型的 [另存新檔] 功能。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|資料|啟用文件的持續性。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|資料|允許隱藏檔案變更事件，例如「重載觸發」。|
