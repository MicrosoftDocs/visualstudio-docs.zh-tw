---
title: 開發舊版語言服務 |Microsoft Docs
description: 瞭解如何在 VSPackage 過程中，或使用 Managed Extensibility Framework (MEF) 擴充功能來執行舊版語言服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59c06c96d2a0263c9e76ed4359e0fac93ab2ab25
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056723"
---
# <a name="develop-a-legacy-language-service"></a>開發舊版語言服務
本節連結的主題可協助您建立舊版語言服務。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語言服務的新方法，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務的模型](../../extensibility/internals/model-of-a-legacy-language-service.md)

 提供核心編輯器的最基礎語言服務模型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 您可以使用此模型作為建立您專屬語言服務的指南。

- [舊版語言服務介面](../../extensibility/internals/legacy-language-service-interfaces.md)

 討論執行語言服務所需的物件，並提供可供您用來提供語法醒目提示、方法資料和其他功能的其他物件清單。

- [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 說明如何將命令篩選器插入您的語言服務中，以攔截文字視圖會以其他方式處理的命令。

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)

 提供如何使用註冊語言服務的相關資訊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [適用于偵錯工具的語言服務支援](../../extensibility/internals/language-service-support-for-debugging.md)

 描述語言服務如何提供支援偵錯工具的功能。

- [檢查清單：建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 提供逐步指示，說明如何建立和整合核心編輯器的語言服務。

## <a name="related-sections"></a>相關章節
- [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 討論如何在您的語言服務中執行語法醒目提示。

- [舊版語言服務中的語句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 討論語句完成，這是語言服務可協助使用者完成已開始鍵入語言關鍵字或元素的程式。

- [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 說明如何提供多載函式和方法的方法提示。

- [如何：在舊版語言服務中提供隱藏文字支援](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 說明隱藏文字區域的目的，並提供有關如何執行隱藏文字區域的指示。

- [如何：在舊版語言服務中提供展開大綱支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 說明針對您的語言擴充大綱支援的兩個選項，而不支援 [折迭 *至定義* ] 命令。
