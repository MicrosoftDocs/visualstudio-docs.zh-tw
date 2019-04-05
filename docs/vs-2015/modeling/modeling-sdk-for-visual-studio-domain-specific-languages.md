---
title: Modeling SDK-網域指定的語言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7bcfe986877305c55f6b459b8c519e4f12f5a503
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "59000484"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modeling SDK for Visual Studio - 網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 Modeling SDK for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK)，您可以建立功能強大的模型為基礎的開發工具，您可以整合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 例如，UML 工具就是使用 MSDK 建立。 同樣地，您可以建立一個或多個模型定義，並將這些定義整合成一組工具。

 MSDK 的核心就是模型定義，您可建立模型定義代表商業領域的概念。 您可以在模型四周放置各種不同的工具，例如圖表檢視、產生程式碼和其他成品的功能、轉換模型的命令，以及與 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的程式碼和其他物件互動的功能。 當您開發模型時，可以將它與其他模型和工具組合成強大的工具組，做為開發工作的重心。

 MSDK 可讓您透過網域指定的語言 (DSL) 的形式迅速開發模型。 一開始是使用專用的編輯器一併定義結構描述或抽象語法與圖形標記法。 VMSDK 會從這個定義產生：

- 模型實作，這個實作具有在交易為基礎的存放區中執行的強類型 API。

- 樹狀檔案總管。

- 圖形編輯器，使用者可在這個編輯器中檢視您定義的模型或模型的一部分。

- 序列化方法，這類方法會將模型儲存為可讀取的 XML。

- 使用文字範本化產生程式碼和其他成品的功能。

  您可以自訂及擴充這些功能。 您的擴充功能會進行整合，整合後仍然可以更新 DSL 定義和重新產生功能，而不會遺失您的擴充功能。

## <a name="samples-and-the-latest-information"></a>範例和最新資訊
 [下載適用於 Visual Studio 2015 SDK 的模型化](http://www.microsoft.com/download/details.aspx?id=48148)

 [範例](http://go.microsoft.com/fwlink/?LinkId=186128)針對模型化 SDK for Visual Studio。

 如需進階的技術和疑難排解的指引，請瀏覽[Visual Studio DSL & Modeling Tools 擴充性論壇](http://go.microsoft.com/fwlink/?LinkID=186074)。

## <a name="in-this-section"></a>本節內容
 [開始使用特定領域語言](../modeling/getting-started-with-domain-specific-languages.md)

 [了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)

 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)

 [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)

 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)

 [了解 DSL 程式碼](../modeling/understanding-the-dsl-code.md)

 [自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)

 [部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)

 [建立 Windows Forms 架構的特定領域語言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [建立 WPF 架構的特定領域語言](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [如何：擴充特定領域語言設計工具](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [支援的 Visual Studio Visualization & Modeling SDK 版本](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [如何：將特定領域語言移轉至新的版本](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Modeling SDK for Visual Studio 的 API 參考](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
