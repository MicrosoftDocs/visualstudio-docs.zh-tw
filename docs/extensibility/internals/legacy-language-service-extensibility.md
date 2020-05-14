---
title: 傳統語言服務可擴充性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707413"
---
# <a name="legacy-language-service-extensibility"></a>舊版語言服務的擴充性
語言服務為編輯 IDE 中的原始碼提供特定於語言的支援。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語言服務的新方法的詳細資訊,請參閱[編輯器和語言服務擴展](../../extensibility/editor-and-language-service-extensions.md)。

 本節討論舊語言服務的結構和實現。

## <a name="in-this-section"></a>本節內容
- [移轉舊版語言服務](../../extensibility/internals/migrating-a-legacy-language-service.md)

 說明如何將語言服務從 Visual Studio 2008 更新到最新版本。

- [舊版語言服務的基本資訊](../../extensibility/internals/legacy-language-service-essentials.md)

 提供有關如何開發語言服務以將程式設計語言整合到 Visual Studio 的重要資訊。

- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)

 提供指向可説明您創建語言服務的主題的連結。

- [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 提供有關在語言服務中支援語法突出顯示的資訊。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 提供有關如何使用託管包框架 (MPF) 在託管代碼中實現全功能語言服務的資訊。

- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 描述使您能夠流覽 IDE 中符號的樹視圖的庫和工具。

## <a name="related-sections"></a>相關章節
- [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)

 提供可視化工作室編輯器的概述。

- [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)

 提供有關可視化工作室調試 SDK 的資訊和連結,其中包含創建和自定義用於調試程式的調試器元件所需的資訊。
