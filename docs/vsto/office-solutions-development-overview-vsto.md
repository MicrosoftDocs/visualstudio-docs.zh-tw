---
title: 'Office 方案開發總覽 (VSTO) '
description: 瞭解如何開發熟悉的 Microsoft Office 使用者介面和工具的自訂專案，例如 Word 中的文字處理功能以及 Excel 的資料分析功能。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9bb964e90c44c4e0b41e0f09df8931665426dc70
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527713"
---
# <a name="office-solutions-development-overview-vsto"></a>Office 方案開發總覽 (VSTO) 
  您可以使用 Microsoft Office 做為方案的前端，以善用熟悉的 Microsoft Office 使用者介面和工具 (例如 Word 的文書處理功能、Excel 的資料分析功能，以及 Outlook 的電子郵件管理功能)。 您可以使用 Visual Studio 來開發方案，以自訂 Office 應用程式，以及加入符合商務流程需求的特定功能。 例如，您可以將 Word 轉變成可將已存在的組件 (這些組件可設定為是否可編輯) 組合為合約的合約產生器。 藉由 Excel，您可以建立自動化的預算工作表，為不同的專案進行自訂。 如果您使用網頁式的架構，則您的使用者也可以離線使用 Office 方案，使複雜的方案比原本可能的更加實用。

 本主題提供 Office 方案類型的概觀，您可以使用由 Visual Studio 中的 Office Developer Tools 所提供的 Visual Studio Tools for Office (VSTO) 範本來建立這些方案。 如需如何使用 Office 進行開發的一般資訊，請參閱 [office 開發人員中心](https://developer.microsoft.com/office)。

## <a name="choose-an-office-project-type"></a>選擇 Office 專案類型
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 提供下列類型的專案範本，用於以 VSTO 為基礎的 Office 程式開發：

- **文件層級自訂** 與特定文件相關聯。

- **VSTO Add-ins** 與應用程式本身相關聯。

  若要決定哪些專案類型最適合您的方案，請考慮您是否只有在特定文件已開啟時才執行程式碼，或是否想要該程式碼在每次應用程式正執行時可供使用。 如需專案範本的詳細資訊，請參閱 [Office 專案範本總覽](../vsto/office-project-templates-overview.md)。

  您可以建立的專案類型，取決於您已安裝在開發電腦上的 Office 應用程式。 如需詳細資訊，請參閱 [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。

### <a name="document-level-customizations"></a>文件層級自訂
 文件層級自訂是由與 Microsoft Office Word 或 Microsoft Office Excel 中的單一文件、活頁簿或範本關聯的組件所組成。 組件會在相關聯的文件開啟時載入。 只有在相關聯的文件開啟時，您才能使用自己建立之自訂中的功能。 自訂不能進行應用程式層範圍的變更，例如在任何文件開啟時顯示新的選單項目或功能區索引標籤。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含可協助您建立文件層級自訂的工具。 您自訂的文件會以設計介面的形式裝載在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，讓您藉由在上面拖放控制項來設計文件。 許多其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 功能也會出現在文件層級專案中，例如 Windows Form 控制項、拖放資料繫結及整合式偵錯工具。

 如需自訂的詳細資訊，請參閱下列主題：

- [開始程式設計 Excel 的檔層級自訂](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [開始程式設計 Word 的檔層級自訂](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO 增益集
 VSTO 增益集是由與 Microsoft Office 應用程式相關聯的組件所組成。 一般而言，VSTO 增益集會在相關聯的應用程式啟動時執行，不過使用者也可以選擇在應用程式已經開始執行後載入 VSTO 增益集。 不論開啟哪一份文件，您所建立之 VSTO 增益集中的功能都可供應用程式本身使用。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含可協助您建立 VSTO 增益集的工具。增益集專案包含自動產生的類別，該類別代表 VSTO 增益集。 這個類別會提供屬性和事件，您可以用來存取主機應用程式的物件模型，並在 VSTO 增益集載入與關閉時執行程式碼。 VSTO 增益集專案也提供許多其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 功能，例如 Windows Form 和整合式偵錯工具。

 如需 VSTO 增益集的詳細資訊，請參閱下列主題：

- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)

- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>使用主要 interop 元件自動化 Office 應用程式
 您可以用程式設計的方式將 Office 應用程式的功能加入方案，方法是撰寫會存取應用程式物件模型的程式碼。 物件模型是一種類別的排列，能夠藉由各種屬性和方法來公開功能。 每個 Office 應用程式的物件模型都不同。

 若要在以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中之 Office 開發工具所建立的方案中，使用 Office 應用程式物件模型，則您必須使用應用程式的主要 Interop 組件 (PIA)。 PIA 可讓您方案中的 Managed 程式碼與 Office 應用程式的 COM 架構的物件模型互動。

 您必須在開發電腦的全域組件快取內安裝並註冊 Office PIA，才能執行大部分的開發工作。 如需詳細資訊，請參閱 [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。 使用者電腦不需要 Office PIA 即可執行 VSTO Office 方案。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

 如需在 VSTO Office 方案中使用 PIA 的詳細資訊，請參閱下列主題：

- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)

- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>在終端使用者電腦上執行 Microsoft VSTO Office 方案
 當您建立 VSTO Office 方案時，請考慮部署需求可能會如何影響您的開發選擇。

### <a name="deployment-options"></a>部署選項
 您可以使用 ClickOnce 或 Windows Installer，部署以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中之 Office 開發工具所建立的方案。 使用 ClickOnce 進行部署可以讓您建立自我更新式方案，其不需有很多使用者互動，即可安裝和執行。 Windows Installer (*.msi*) 檔案可以輕鬆地散發至使用者電腦，或使用 Systems Management SERVER (SMS) 散發。 如需部署 VSTO Office 方案的詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

### <a name="install-prerequisites"></a>安裝先決條件
 使用者在執行您以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中的 Office 開發工具建立的方案之前，必須已在電腦上安裝某些必要條件。 如果您使用 ClickOnce 或透過建立 Windows Installer 檔案來部署方案，則這些必要條件可以隨方案一起安裝。 如需詳細資訊，請參閱 [office 方案的部署必要條件](/previous-versions/bb608617(v=vs.110)) 和 [如何：在終端使用者電腦上安裝必要條件以執行 Office 解決方案](/previous-versions/bb608608(v=vs.110))。

### <a name="security"></a>安全性
 VSTO Office 方案的安全性是透過 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 在安裝和載入方案時進行的一系列檢查來強制執行。 這些檢查包括確認是否信任部署資訊清單的位置，或是否信任用於簽署部署資訊清單的憑證。 如需詳細資訊，請參閱 [安全的 Office 方案](../vsto/securing-office-solutions.md)。

## <a name="see-also"></a>另請參閱
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [開始程式設計 Excel 的檔層級自訂](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [開始程式設計 Word 的檔層級自訂](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
