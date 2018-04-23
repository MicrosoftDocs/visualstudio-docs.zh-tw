---
title: 服務延伸的編輯器和語言 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2fceb0487c23dc34d3f4f4937d7a5998340ae3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="editor-and-language-service-extensions"></a>編輯器和語言服務延伸模組
您可以擴充 Visual Studio 程式碼編輯器的大部分功能。 編輯器以 Windows Presentation Foundation (WPF) 為基礎，而以 managed 程式碼撰寫。 雖然此設計不同於在舊版的 Visual Studio 中的設計，它會提供大部分相同的功能。 若要擴充編輯器 中，使用 Managed Extensibility Framework (MEF)。  
  
 Visual Studio SDK 提供配接器稱為*填充碼*以支援較早版本所撰寫的 Vspackage。 不過，如果您有現有的 VSPackage，建議其更新為新的技術，以取得更佳的效能和可靠性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)|若要使用編輯器項目範本的簡介。|  
|[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)|導入的設計和核心編輯器的功能，並示範如何延伸該架構的文件連結。|  
|[在編輯器中的傳統介面](../extensibility/legacy-interfaces-in-the-editor.md)|說明如何從現有的程式碼存取核心編輯器文件的連結。|  
|[建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)|說明如何建立自訂編輯器的文件的連結。|  
|[舊版語言服務的擴充性](../extensibility/internals/legacy-language-service-extensibility.md)|描述如何將程式語言整合到 Visual Studio 的文件的連結。|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|導入了 Managed 的 Extensibility Framework (MEF)。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|導入了 Windows Presentation Foundation (WPF)。|