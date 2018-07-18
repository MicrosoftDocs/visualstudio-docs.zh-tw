---
title: 舊版語言服務擴充性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7d8165060fa3b9a6445ad71a977c79414056f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129718"
---
# <a name="legacy-language-service-extensibility"></a>舊版語言服務擴充性
語言服務提供編輯原始程式碼，IDE 中的特定語言的支援。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
 本節討論的結構與舊版語言服務實作。  
  
## <a name="in-this-section"></a>本節內容  
 [移轉舊版語言服務](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 說明如何更新語言服務從 Visual Studio 2008 的最新版本。  
  
 [舊版語言服務的基本資訊](../../extensibility/internals/legacy-language-service-essentials.md)  
 提供有關如何開發整合到 Visual Studio 程式設計語言的語言服務的重要資訊。  
  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)  
 提供主題連結，可協助您建立語言服務。  
  
 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 提供關於支援語法反白顯示語言服務中的資訊。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有關如何使用 managed 的 package framework (MPF) 來實作在 managed 程式碼的完整語言服務的資訊。  
  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 描述程式庫和工具，可讓您瀏覽樹狀檢視，在 IDE 中的符號。  
  
## <a name="related-sections"></a>相關章節  
 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)  
 提供 Visual Studio 編輯器的概觀。  
  
 [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)  
 提供 Visual Studio 偵錯 SDK，其中包含的資訊，才能建立和自訂用於偵錯程式的偵錯工具元件的相關資訊和連結。