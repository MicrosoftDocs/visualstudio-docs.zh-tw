---
title: 編輯器和語言服務延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5512aa9fc40e9f2ef7619cc5cf80f2751de15327
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265966"
---
# <a name="editor-and-language-service-extensions"></a>編輯器和語言服務延伸模組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以擴充 Visual Studio 程式碼編輯器的大部分功能。 編輯器以 Windows Presentation Foundation (WPF) 為基礎，並撰寫 managed 程式碼中。 雖然這項設計會不同於在舊版的 Visual Studio 中的設計，它會提供的大部分相同的功能。 若要擴充編輯器，使用 Managed Extensibility Framework (MEF)。  
  
 Visual Studio SDK 提供稱為介面卡*填充碼*支援是針對較早版本所撰寫的 Vspackage。 不過，如果您有現有的 VSPackage，建議其更新為新的技術，來取得較佳的效能和可靠性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)|使用編輯器項目範本的簡介。|  
|[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)|介紹設計和核心編輯器的功能，並說明如何擴充它的文件連結。|  
|[編輯器中的舊版介面](../extensibility/legacy-interfaces-in-the-editor.md)|說明如何從現有的程式碼存取核心編輯器的文件的連結。|  
|[建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)|說明如何建立自訂編輯器的文件的連結。|  
|[舊版語言服務的擴充性](../extensibility/internals/legacy-language-service-extensibility.md)|說明如何整合到 Visual Studio 的程式設計語言的文件的連結。|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|導入了 Managed 的 Extensibility Framework (MEF)。|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|介紹 Windows Presentation Foundation (WPF)。|

