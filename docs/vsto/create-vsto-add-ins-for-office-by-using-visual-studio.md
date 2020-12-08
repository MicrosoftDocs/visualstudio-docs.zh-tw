---
title: 使用 Visual Studio 建立適用於 Office 的 VSTO 增益集
description: 瞭解如何使用 Visual Studio 中的 Microsoft Office 開發人員工具，建立可延伸 Office 的 .NET Framework 應用程式。
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 50337b728647b5e15a877216713cd6fc9823742a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847971"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>使用 Visual Studio 建立適用於 Office 的 VSTO 增益集
  您可以使用 Visual Studio 中的 Microsoft Office Developer Tools 來建立 .NET Framework 應用程式，以擴充 Office 功能。 這些應用程式也稱為 *「Office 方案」*(Office Solution)。

 Office 開發人員工具提供的功能，可協助您針對各種商務需求來建立 Office 方案。 這些工具包含可協助您使用 Visual Basic 或 Visual C# 建立 Office 方案的專案範本，以及可協助您為 Office 方案建立自訂使用者介面的視覺化設計工具。

[!include[Add-ins note](includes/addinsnote.md)]

 如需有關 Office 程式開發的最新資訊，請參閱 [Microsoft Office 開發人員中心](https://developer.microsoft.com/office/docs)。

## <a name="in-this-section"></a>本節內容
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](getting-started-office-development-in-visual-studio.md)

 提供有關如何設定開發電腦以建立 Office 方案、如何開始建立 Office 方案，以及 Visual Studio 中 Office 開發新功能的資訊連結。

- [升級和遷移 Office 方案](upgrading-and-migrating-office-solutions.md)

 提供有關使用舊版 Visual Studio 所建立的專案之升級程序的資訊連結。

- [Visual Studio 中的 Office 方案架構](architecture-of-office-solutions-in-visual-studio.md)

 提供有關 Office 方案運作方式的資訊連結，包括文件層級自訂和 VSTO 增益集的相關資訊。

- [設計和建立 Office 方案](designing-and-creating-office-solutions.md)

 提供有關如何在 Visual Studio 中建立 Office 專案及設定專案的資訊。

- [開發 Office 方案](developing-office-solutions.md)

 提供有關如何搭配使用 Managed 程式碼和 Office 方案的資訊，包括如何自訂 Office 使用者介面、使用資料及疑難排解問題。

- [Excel 方案](excel-solutions.md)

 提供有關如何自動化 Excel、建立 Excel 方案及了解 Excel 特有之全球化問題的資訊。

- [InfoPath 解決方案](infopath-solutions.md)

 提供有關如何建立 InfoPath 之表單範本與 VSTO 增益集的資訊。

- [Outlook 方案](outlook-solutions.md)

 提供有關如何自動化 Outlook 以及建立 Outlook VSTO 增益集和表單區域的資訊。

- [PowerPoint 方案](powerpoint-solutions.md)

 提供有關如何自動化 PowerPoint 以及建立 PowerPoint VSTO 增益集的資訊。

- [專案解決方案](project-solutions.md)

 提供有關如何自動化 Microsoft Office 專案及建立 project VSTO 增益集的資訊。

- [Visio 方案](visio-solutions.md)

 提供有關如何自動化 Visio 以及建立 Visio VSTO 增益集的資訊。

- [Word 方案](word-solutions.md)

 提供有關如何自動化 Word 以及建立 Word 方案的資訊。

- [建立 Office 方案](building-office-solutions.md)

 提供有關建置 Office 專案與 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中其他類型專案之間差異的資訊。

- [Debug Office 專案](debugging-office-projects.md)

 提供有關偵錯 Office 專案和 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中其他類型專案之間差異的資訊。

- [保護 Office 方案](securing-office-solutions.md)

 提供有關安全性功能在 Office 方案中運作方式的資訊。

- [部署 Office 方案](deploying-an-office-solution.md)

 提供有關如何讓使用者使用 Office 方案，以及選擇部署方法時所要考慮之主要問題的資訊。

- [Office 開發範例和逐步解說](office-development-samples-and-walkthroughs.md)

 提供範例應用程式連結，以及逐步指示如何執行一般工作的主題連結。

- [在 Visual Studio&#41;中 &#40;Office 開發的一般參考 ](general-reference-office-development-in-visual-studio.md)

 提供有關 Office 主要 interop 元件、資訊清單、使用者介面元素和錯誤訊息的詳細資訊連結。

- [在 Visual Studio&#41;中 &#40;Office 開發的受控參考 ](managed-reference-office-development-in-visual-studio.md)

 提供有關以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標的 Office 專案所使用之 API 命名空間和類型的資訊連結。 如需有關以 .NET Framework 3.5 為目標的 Office 專案所使用之命名空間和類型的 API 參考檔，請參閱 Visual Studio 2008 檔中的下列參考章節： [2007 系統管理的參考](managed-reference-office-development-in-visual-studio.md)。

- [在 Visual Studio&#41;中 &#40;Office 開發的非受控 API 參考 ](unmanaged-api-reference-office-development-in-visual-studio.md)

 包含 COM 介面的相關資訊連結，您可以使用這些介面來執行載入及卸載 Office 應用程式中受管理之 VSTO 增益集等動作。

## <a name="related-sections"></a>相關章節
- [使用 Visual Studio 開發人員入口網站進行 Office 開發](https://developer.microsoft.com/office/docs) 提供其他資源，例如技術文章、影片和 blog。

- [Visual Studio 開發人員中心](https://visualstudio.microsoft.com/) 提供其他 Visual Studio 資源，例如技術文章、影片和 blog。

- [MSDN library 的 Microsoft Office 開發] 區段](/previous-versions/office/office-12/bb726434(v=office.12)) MSDN library 的區域，您可以在其中找到有關開發數個 Office 版本之方案的文章和參考檔， (不是使用 Visual Studio) 的 Office 程式開發專用。

- [Visual Studio 中的應用程式開發](/previous-versions/h8w79z10(v=vs.140)) 包含主題的連結，說明如何使用 Visual Studio 來設計、開發、偵測和部署 web 應用程式、XML web service 和傳統用戶端應用程式。

- [Visual Studio 中的 .NET Framework 程式設計](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) 討論在 Visual Basic 和 Visual c # 中使用 .NET Framework 的應用程式開發。