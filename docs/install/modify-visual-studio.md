---
title: 修改 Visual Studio 2017
titleSuffix: ''
description: 了解如何逐步修改 Visual Studio。
ms.date: 02/10/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 57aa5531eb6d6517b520991ababefc38b25a9a2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77125347"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>透過新增或移除工作負載和元件來修改 Visual Studio

::: moniker range="vs-2019"

因為修改 Visual Studio 很容易，所以在您需要它時，它只包含您需要的內容。 若要執行修改作業，請開啟 Visual Studio 安裝程式來新增或移除工作負載和元件。

::: moniker-end

::: moniker range="vs-2017"

我們不僅讓您可以更輕鬆地將 Visual Studio 個人化以配合您要完成的工作，也讓您可以更輕鬆地自訂 Visual Studio。 為此，打開新的視覺化工作室安裝程式並進行所需的更改。

::: moniker-end

方法如下。

>[!IMPORTANT]
>若要安裝、更新或修改 Visual Studio，您必須以具有系統管理權限的帳戶登入。 有關詳細資訊，請參閱[使用者許可權和視覺化工作室](../ide/user-permissions-and-visual-studio.md)。

>[!NOTE]
> 以下過程假定您有互聯網連接。
>
> 如需如何修改先前所建立 Visual Studio [離線安裝](create-an-offline-installation-of-visual-studio.md)的詳細資訊，請參閱[更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)頁面和[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)頁面。

## <a name="open-the-visual-studio-installer"></a>打開視覺化工作室安裝程式

::: moniker range="vs-2017"

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行 Windows 10，的電腦上，選取 [開始]****，然後捲動到字母 [V]****，它在其中列為 [Visual Studio Installer]****。

     ![視覺化工作室安裝程式](media/locate-the-visual-studio-installer.png "查找微軟視覺化工作室安裝程式")

     >[!TIP]
     >在某些電腦上，Visual Studio 安裝程式可能會列在 **"M"** 字母下方，成為 [Microsoft Visual Studio 安裝程式]****。<br/><br/> 您也可以在下列位置找到 Visual Studio 安裝程式：`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 打開安裝程式，然後選擇 **"修改**"。

     ![啟動或修改視覺工作室](media/modify-visual-studio.png "修改 Visual Studio 2017")

     > [!IMPORTANT]
     > 如果您有擱置的更新，則 [修改] 按鈕會在不同的位置。 因此，您可以修改而不需要更新 Visual Studio (如果您選擇這麼做)。 按一下 [更多]****，然後選擇 [修改]****。
     >
     > ![更新或修改 Visual Studio](media/modify-or-update-visual-studio.png "更新或修改視覺工作室 2017")

::: moniker-end

::: moniker range="vs-2019"

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行 Windows 10，的電腦上，選取 [開始]****，然後捲動到字母 [V]****，它在其中列為 [Visual Studio Installer]****。

     ![在 Windows 上開啟 Visual Studio 安裝程式](media/vs-2019/vs-installer-windows-start.png "打開視覺化工作室安裝程式")

     > [!NOTE]
     > 您也可以在下列位置找到 Visual Studio 安裝程式：
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    您可能需要更新安裝程式才能繼續。 若是如此，請遵循提示。

1. 請在安裝程式中尋找您安裝的 Visual Studio 版本，然後選擇 [修改]****。

     ![更新或修改 Visual Studio](media/vs-2019/vs-installer-modify.png "更新或修改視覺工作室 2019")

     > [!IMPORTANT]
     > 如果您有擱置的更新，則 [修改] 按鈕會在不同的位置。 這樣，您可以修改 Visual Studio 而不更新它，如果您願意。 選擇**更多**，然後選擇 **"修改**"。
     >
     > ![更新或修改 Visual Studio](media/vs-2019/modify-update-visual-studio.png "更新或修改視覺工作室 2019")

::: moniker-end

## <a name="modify-workloads"></a>修改工作負載

::: moniker range="vs-2017"

 [工作負載](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/)包含您使用的程式設計語言或平臺所需的功能。 您可以使用工作負載來修改 Visual Studio，以便在需要時支援您要執行的工作。

1. 在"視覺化工作室安裝程式"中，選擇 **"工作負載"** 選項卡，然後選擇或取消選擇所需的工作負荷。

    ![Visual Studio 2017 安裝對話方塊](media/modify-workloads.png "選擇 Visual Studio 2019 中的工作負載")

1. 選擇接受預設的 [在下載時安裝]**** 選項還是 [全部下載後安裝]**** 選項。

    ![視覺化工作室 2017 設置選項](media/vs-2019/vs-installer-choose-install-or-download.png "選擇在下載時安裝，或先下載，稍後安裝")

    如果您想要下載後再安裝，則 [全部下載後安裝] 選項會很方便。

1. 選擇 [修改]****。

1. 安裝新工作負載後，從視覺化工作室安裝程式中選擇 **"啟動"** 以打開視覺化工作室。

::: moniker-end

::: moniker range="vs-2019"

 工作負載包含您使用之程式設計語言或平台所需的功能。 您可以使用工作負載來修改 Visual Studio，以便在需要時支援您要執行的工作。

 > [!TIP]
>有關開發所需的工具和元件捆綁包的詳細資訊，請參閱[Visual Studio 工作負載](https://visualstudio.microsoft.com/vs/#workloads)。

1. 在"視覺化工作室安裝程式"中，選擇 **"工作負載"** 選項卡，然後選擇或取消選擇所需的工作負荷。

    ![視覺化工作室 2019 設置對話方塊](media/vs-2019/vs-installer-modify-workloads.png "選擇 Visual Studio 2019 中的工作負載")

1. 選擇接受預設的 [在下載時安裝]**** 選項還是 [全部下載後安裝]**** 選項。

    ![視覺化工作室 2019 設置選項](media/vs-2019/vs-installer-choose-install-or-download.png "選擇在下載時安裝，或先下載，稍後安裝")

    如果您想要下載後再安裝，則 [全部下載後安裝] 選項會很方便。

1. 選擇 [修改]****。

1. 安裝新工作負載後，從視覺化工作室安裝程式中選擇 **"啟動"** 以打開視覺化工作室。

::: moniker-end

## <a name="modify-individual-components"></a>修改個別元件

如果不想使用工作負載自訂 Visual Studio 安裝，請在"視覺化工作室安裝程式"中選擇 **"單個元件**"選項卡，選擇所需的元件，然後按照提示操作。

>[!TIP]
> 有關 SQL 伺服器資料工具 （SSDT） 元件的資訊，請參閱[為 Visual Studio 下載並安裝 SSDT](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15)。

## <a name="modify-language-packs"></a>修改語言包

預設情況下，安裝程式在首次運行時與作業系統的語言匹配。 但是，您可以隨時更改語言。 為此，請在"視覺化工作室安裝程式"中選擇 **"語言包**"選項卡，選擇您喜歡的語言，然後按照提示進行操作。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 工作負載與元件識別碼清單](workload-and-component-ids.md)
* [更新 Visual Studio](update-visual-studio.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
* [在維護基底上時更新 Visual Studio](update-servicing-baseline.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
