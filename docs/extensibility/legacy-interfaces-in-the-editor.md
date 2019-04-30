---
title: 在編輯器中的舊版介面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 044bf36845be70290291b79dee255c452f56f0a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907472"
---
# <a name="legacy-interfaces-in-the-editor"></a>在編輯器中的舊版介面
您可以從舊版的介面來存取 Visual Studio 編輯器。 Visual Studio SDK 包含配接器稱為*填充碼*，可讓這些新的編輯器與互動的介面。 不過，我們建議您更新您舊版的程式碼，以使用新的編輯器 API。 您的程式碼會比較好，而且您可以使用新的技術，例如 Windows Presentation Foundation (WPF) 和 Managed Extensibility Framework (MEF)。

## <a name="related-topics"></a>相關主題

| 標題 | 描述 |
| - | - |
| [調整傳統的程式碼編輯器](../extensibility/adapting-legacy-code-to-the-editor.md) | 說明如何調整到新的編輯器程式碼。 |
| [新增或變更的行為，與編輯器的介面卡](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | 說明如何編輯器配接器的行為不同於舊版的編輯器。 |
| [在核心編輯器](../extensibility/inside-the-core-editor.md) | 描述舊版編輯器的不同元件。 |
| [使用舊版 API 具現化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | 說明如何使用舊版的 API 來具現化核心編輯器。 |
| [編輯器 factory](../extensibility/editor-factories.md) | 說明如何在舊版的 API 中使用編輯器 factory。 |
| [如何：登錄編輯程式檔案類型](../extensibility/how-to-register-editor-file-types.md) | 說明如何將檔案的副檔名連結到您的編輯器。 |
| [逐步解說：編輯器建立一個核心，並登錄編輯器的檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | 說明如何建立核心編輯器，並連結至該檔案的副檔名。 |
| [如何：編輯器提供的內容](../extensibility/how-to-provide-context-for-editors.md) | 說明如何針對您的編輯器提供的內容。 |
| [語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md) | 說明語言服務及編輯器之間的互動。 |
| [使用舊版的 API 來存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | 說明如何使用舊版 API 存取的文字緩衝。 |
| [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | 說明如何使用舊版的 API 來存取 [文字] 檢視。 |
| [使用舊版 API 來自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | 說明如何使用舊版 API 來自訂程式碼視窗。 |
| [使用舊版 API 存取文字圖層](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | 說明如何使用舊版的 API 來存取不同圖層上的文字。 |
| [在舊版的 API 中使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md) | 說明如何使用舊版 API 中新增文字標記。 |
| [使用舊版 API 自訂編輯器控制項及功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | 說明如何使用舊版 API 來自訂編輯器控制項。 |
| [管理復原和取消復原使用舊版的 API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | 說明如何管理復原和取消復原使用舊版 API。 |
| [如何：實作尋找和取代機制](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | 說明如何管理 尋找和取代使用舊版 API。 |
| [如何：隱藏檔案變更通知](../extensibility/how-to-suppress-file-change-notifications.md) | 說明如何使用舊版 API 隱藏檔案變更通知。 |
| [建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md) | 說明如何建立自訂編輯器和設計工具。 |
| [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md) | 提供功能，以提供自訂功能的相關文件的連結[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]藉由新增語言服務支援的核心編輯器。 |
| [使用字型和色彩](../extensibility/using-fonts-and-colors.md) | 說明如何使用舊版的介面中的字型和色彩。 |
