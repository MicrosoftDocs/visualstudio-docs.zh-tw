---
title: 編輯器和語言服務延伸模組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09456c67eea98947f182e5ab3b3c90fd21a7a7c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011061"
---
# <a name="editor-and-language-service-extensions"></a>編輯器和語言服務延伸模組
您可以擴充 Visual Studio 程式碼編輯器的大部分功能。 編輯器以 Windows Presentation Foundation (WPF) 為基礎，並撰寫 managed 程式碼中。 雖然這項設計會不同於在舊版的 Visual Studio 中的設計，它會提供的大部分相同的功能。 若要擴充編輯器，使用 Managed Extensibility Framework (MEF)。  
  
 Visual Studio SDK 提供稱為介面卡*填充碼*支援是針對較早版本所撰寫的 Vspackage。 不過，如果您有現有的 VSPackage，建議其更新為新的技術，來取得較佳的效能和可靠性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)|使用編輯器項目範本的簡介。|  
|[編輯器和語言服務延伸](../extensibility/extending-the-editor-and-language-services.md)|介紹設計和核心編輯器的功能，並說明如何擴充它的文件連結。|  
|[在編輯器中的舊版介面](../extensibility/legacy-interfaces-in-the-editor.md)|說明如何從現有的程式碼存取核心編輯器的文件的連結。|  
|[建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)|說明如何建立自訂編輯器的文件的連結。|  
|[舊版語言服務擴充性](../extensibility/internals/legacy-language-service-extensibility.md)|說明如何整合到 Visual Studio 的程式設計語言的文件的連結。|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|導入了 Managed 的 Extensibility Framework (MEF)。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|介紹 Windows Presentation Foundation (WPF)。|