---
title: 設計和建立 Office 方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b939640b0676ae34eedeed96c8a4b6b21a5a37e4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599515"
---
# <a name="design-and-create-office-solutions"></a>設計和建立 Office 方案

Visual Studio 提供您可用來建立幾種不同類型之 Office 方案的專案範本。 文件的本節描述此專案範本，並提供有關建立 Office 專案的指引。 如需如何實作自訂程式碼和使用者介面，在您建立專案之後，請參閱[開發 Office 方案](../vsto/developing-office-solutions.md)。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> 想要開發解決方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集較小的使用量，相較於 VSTO 增益集和解決方案，而且您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3、 以及 XML 來建置。

## <a name="create-office-projects"></a>建立 Office 專案
 在開始之前，您應該判斷您的需求，並探索能提供最適合之方案的類型。 例如，如果您每次使用應用程式時，都必須執行 Office 方案，則 VSTO 增益集對您的需求最為適合。 如果程式碼與單一文件緊密整合，則請建立文件層級的自訂。 這些專案類型可做為 Visual Studio 專案範本提供使用。 如需隨附於 Visual Studio 的 Office 專案範本的詳細資訊，請參閱[Office 專案範本概觀](../vsto/office-project-templates-overview.md)。 如需如何建立 Office 專案的詳細資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

 Office 專案具有不同於其他 Visual Studio 之專案類型的功能和專案項目。 例如，當您建立文件層級專案時，專案中的文件或活頁簿可以在 Visual Studio 內開啟和編輯。 如需詳細資訊，請參閱 < [Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。

## <a name="choose-a-net-framework-version"></a>選擇 .NET Framework 版本
 選取最符合您需求的專案類型後，您可以選擇要在開發程序中使用的 .NET Framework 版本。 您可以下列 Office 專案中的 .NET Framework 版本為目標：

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  針對方案執行的終端使用者電腦上需要您選擇專案的.NET Framework 版本。 例如，如果您專案的目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，則[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]需要使用者電腦上。 在此範例中，如果只在使用者電腦上安裝.NET Framework 3.5，不會執行您的解決方案。

  如果您移轉以 .NET Framework 3.5 為目標的 VSTO 增益集專案，Visual Studio 便會將您專案的目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，視您已安裝的 Office 版本而定。

  不過，Visual Studio 將目標變更為 Framework 之後，如果專案中的某些程式碼會使用特定功能，則您可能需要修改此程式碼。 如需如何變更目標 framework 的詳細資訊，請參閱[How to:以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。 如需您可能需要您在專案中變更的相關資訊，請參閱[設為.NET Framework 4 或更新版本的移轉 Office 方案](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)。

  如果 Visual Studio 會變更您的專案的目標.NET Framework，而且您使用 ClickOnce 來部署您的解決方案，請確定也選取對應中的.NET Framework 版本**必要條件** 對話方塊。 當您為專案變更此目標 Framework 時，選取此選項並不會自動變更。 如需詳細資訊，請參閱[如何：安裝必要條件來執行 Office 方案的使用者電腦上](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。

> [!NOTE]
>  在使用 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 建立的 Office 專案中，您無法以 .NET Framework 3.5 或更早版本為目標。 您使用 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 建立的 Office 專案需要 [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] 中首次推出的功能。

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>了解使用者電腦上需要 Office Pia 時
 根據預設，Office 主要 interop 組件 (Pia) 不需要安裝在使用者電腦上，如果**內嵌 Interop 類型**專案中的每個 Office PIA 參考的屬性設定為 **，則為 True**，這是預設值。 在此情節中，您的方案所使用的 PIA 類型的類型資訊會在建置專案時嵌入至方案組件。 在執行階段，內嵌的類型資訊用而非使用 Pia，來呼叫 Office 應用程式的 COM 架構物件模型。 如需 Pia 類型如何內嵌至您的解決方案的詳細資訊，請參閱[類型等價和內嵌 interop 類型](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)。

 如果**內嵌 Interop 類型**專案中的每個 Office PIA 參考的屬性設定為**False**，必須安裝並在每個使用者電腦的全域組件快取中註冊 Office Pia，執行方案。 在大部分情況下，PIA 為 Office 的預設安裝，但是您也可以包含 PIA 可轉散發套件做為方案的必要條件。 如需詳細資訊，請參閱 < [Office 方案的部署必要條件](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)。

### <a name="understand-the-client-profile"></a>了解 client profile
 .NET Framework Client Profile 是完整 .NET Framework 的子集。 如果您只需要使用 .NET Framework 中的用戶端功能，而且想要提供 Office 方案的最快速部署經驗，則可以將 .NET Framework Client Profile 當做目標。 如需詳細資訊，請參閱 < [.NET Framework client profile](/dotnet/framework/deployment/client-profile)。

 當您建立以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 為目標的 Office 專案時，根據預設會以 [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] 為目標。 如果要針對完整 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 開發，您必須在建立專案之後設定這個選項。 如需詳細資訊，請參閱[如何：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>建立 64 位元版本的 Microsoft Office 解決方案
 Microsoft Office 提供 64 位元和 32 位元的版本。 若要建立可以在任一版本中執行的 Office 方案，平台目標設定為您的專案必須設定為**任何 CPU**。 這是 Office 專案的預設值。 如需詳細資訊，請參閱 <<c0> [ 建置 Office 方案](../vsto/building-office-solutions.md)。

 個別之 64 位元和 32 位元版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可由 64 位元和 32 位元版本的 Microsoft Office 所使用。 如需詳細資訊，請參閱 < [Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

## <a name="assemblies-in-office-solutions"></a>在 Office 方案中的組件
 當您在 Visual Studio 中使用 Office 開發工具建立 Office 專案時，您所撰寫的程式碼最後會編譯成組件。 組件部署到共用的伺服器或用戶端電腦上的目錄。

 Office 方案中的組件由 Office 應用程式所載入。 載入組件之後，組件中的程式碼可以回應在應用程式中引發的事件，例如，當使用者按一下功能表項目時。 組件中的程式碼可以呼叫物件模型，藉此自動化和擴充應用程式，而且可以使用 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] 中的任何類別。 如需詳細資訊，請參閱 <<c0> [ 文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)並[Architecture of VSTO 增益集](../vsto/architecture-of-vsto-add-ins.md)。

 Office 方案使用部署資訊清單和應用程式資訊清單來識別組件。 資訊清單包含組件的名稱、版本和位置的相關資訊，因此應用程式可以尋找、連結和執行正確的組件。 如需詳細資訊，請參閱 <<c0> [ 應用程式和部署資訊清單在 Office 方案中](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

 文件層級專案包含文件以及組件。 文件可做為應用程式的前端，而且是所有使用者互動發生的位置。 每份文件只可以有一個主要專案組件與其相關聯；不過，多份文件可以指向相同的組件。

 文件層級專案中的組件不會內嵌在文件中；相反地，它們存放在其他位置，並由此文件的應用程式資訊清單所識別。

## <a name="security-considerations-for-assemblies"></a>組件的安全性考量
 如需在電腦上執行 Office 方案，方案所使用的組件必須為受信任才可執行。 如需有關安全性的詳細資訊，請參閱 <<c0> [ 保護的 Office 方案](../vsto/securing-office-solutions.md)。

 根據預設，方案組件以及任何位在專案輸出資料夾中的參考組件都會受到信任，能夠在您建置專案時於開發電腦上執行。 如需詳細資訊，請參閱 <<c0> [ 建置 Office 方案](../vsto/building-office-solutions.md)。

 基於安全性理由，最好能在您的本機電腦上建立專案，而不要在共用的位置上進行開發。 如需詳細資訊，請參閱 < [Office 方案的共同開發](../vsto/collaborative-development-of-office-solutions.md)。

## <a name="referenced-assemblies"></a>參考的組件
 組件可以參考列入專案參考中的其他組件。 不過，一個文件層級的專案組件不能參考另一個文件層級的專案組件。

## <a name="see-also"></a>另請參閱
- [Office 專案範本概觀](../vsto/office-project-templates-overview.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [在 Visual Studio 環境中的 office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Office 專案中的屬性](../vsto/properties-in-office-projects.md)
- [執行不同版本的 Microsoft Office 中的方案](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [如何：透過主要 interop 組件的目標 Office 應用程式](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [在 Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [如何：設定 Office 方案的組態資訊](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [使用 Visual studio 的 Office 功能](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [在 Office 程式設計中的一般工作](../vsto/common-tasks-in-office-programming.md)
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [在 Visual Studio 中的 Office 方案的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
