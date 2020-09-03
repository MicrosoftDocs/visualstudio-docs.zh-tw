---
title: 舊版語言服務擴充性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194991"
---
# <a name="legacy-language-service-extensibility"></a>舊版語言服務的擴充性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

語言服務提供在 IDE 中編輯原始程式碼的語言特定支援。  
  
 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語言服務的新方法，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
 本節討論舊版語言服務的結構和執行。  
  
## <a name="in-this-section"></a>本節內容  
 [移轉舊版語言服務](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 說明如何將語言服務從 Visual Studio 2008 更新為最新版本。  
  
 [舊版語言服務的基本資訊](../../extensibility/internals/legacy-language-service-essentials.md)  
 提供有關如何開發語言服務以將程式設計語言整合至 Visual Studio 的重要資訊。  
  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)  
 提供可協助您建立語言服務的主題連結。  
  
 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 提供在語言服務中支援語法醒目提示的相關資訊。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有關如何使用 managed package framework (MPF) 在 managed 程式碼中執行功能完整的語言服務的資訊。  
  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 描述程式庫和工具，可讓您在 IDE 中流覽符號的樹狀檢視。  
  
## <a name="related-sections"></a>相關章節  
 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)  
 提供 Visual Studio 編輯器的總覽。  
  
 [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)  
 提供 Visual Studio 偵錯工具的相關資訊和連結，其中包含建立和自訂用來偵測程式之偵錯工具元件所需的資訊。
