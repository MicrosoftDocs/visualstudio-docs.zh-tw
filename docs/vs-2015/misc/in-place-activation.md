---
title: 就地啟用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 9c673fd7eb2b51e611256efb427baa0174d29462
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940767"
---
# <a name="in-place-activation"></a>在就地啟用
如果您的編輯器檢視主控 ActiveX 或其他主動式控制項，您必須實作編輯器檢視，作為 ActiveX 控制項或是作為使用就地啟用模型的主動式文件資料物件。  
  
## <a name="support-for-menus-toolbars-and-commands"></a>功能表、工具列和命令的支援  
 Visual Studio 可讓您的編輯器檢視使用 IDE 的功能表和工具列。 這些延伸稱為 *OLE 就地元件*。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>。  
  
 如果您實作 ActiveX 控制項，您可以主控其他內嵌的物件。 如果您實作文件資料物件，視窗框架會限制您使用 ActiveX 控制項的能力。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> 介面允許分開資料和檢視。 不過，Visual Studio 不支援這項功能，而且這些介面只會用來代表文件檢視物件。  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 服務的編輯器，可以藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 介面的方法來提供功能表、工具列和命令整合；此介面是由 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 服務所實作。 編輯器也可以提供其他 Visual Studio 功能，例如選取項目追蹤和復原管理。 如需詳細資訊，請參閱 <<c0> [ 建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)。  
  
## <a name="objects-and-interfaces-used"></a>使用的物件與介面  
 下圖中顯示用來建立就地啟用的物件。  
  
 ![在&#45;將啟動編輯器](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
就地啟用編輯器  
  
> [!NOTE]
>  在此繪圖的物件中，建立標準的編輯器只需要 `CYourEditorFactory` 物件。 如果您要建立自訂編輯器，您不需要實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ，因為您的編輯器可能有自己的私用持續性機制。 如需詳細資訊，請參閱 <<c0> [ 建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)。  
  
 實作來建立就地啟用編輯器的所有介面，顯示在單一 `CYourEditorDocument` 物件上，但這項組態只支援文件資料的單一檢視。 如需支援文件資料之多個檢視的詳細資訊，請參閱 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)。  
  
|介面|物件的類型|使用|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|檢視|讓就地 VSPackage 物件能使用 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 服務，作為完整整合的 IDE 元件來運作。 這項服務將物件的功能表、工具列和命令整合到 IDE，並發出狀態變更的通知。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|檢視|內嵌的物件提供基本功能給其容器並與其通訊的主要方式。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|檢視|管理就地物件的啟用和停用，並判斷應該可看見就地物件的多少部分。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|檢視|在就地物件、相關應用程式最外層框架視窗和包含內嵌物件之應用程式的文件視窗之間，提供直接的通訊通道。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|檢視|實作 ActiveX 物件。 請注意，IDE 中不使用分開文件資料和檢視的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> 和 `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` 方法。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|檢視/資料|可讓文件資料物件或文件檢視物件參與命令處理，或兩者皆可參與。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|檢視|啟用狀態列更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|檢視|啟用將項目加入工具箱。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|資料|傳送編輯檔案的變更通知。 (這個介面是選擇性的。)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|資料|用來啟用檔案類型的 [另存新檔] 功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|資料|啟用文件的持續性。 針對唯讀檔案，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> 以提供「鎖定」圖示，表示唯讀檔案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|資料|決定是否應該忽略文件資料的變更。|