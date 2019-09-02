---
title: 修改 Visual Studio 2017
titleSuffix: ''
description: 了解如何逐步修改 Visual Studio。
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 08/23/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a97db7e6b81eb9e807902d1b9bd0ea8ee6efa55e
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026482"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>透過新增或移除工作負載和元件來修改 Visual Studio

::: moniker range="vs-2019"

因為修改 Visual Studio 很容易，所以在您需要它時，它只包含您需要的內容。 若要執行修改作業，請開啟 Visual Studio 安裝程式來新增或移除工作負載和元件。

::: moniker-end

::: moniker range="vs-2017"

我們不僅讓您可以更輕鬆地將 Visual Studio 個人化以配合您要完成的工作，也讓您可以更輕鬆地自訂 Visual Studio。 若要這樣做，請啟動新的 Visual Studio 安裝程式並進行所需的變更。

::: moniker-end

方式如下：

>[!IMPORTANT]
>若要安裝、更新或修改 Visual Studio，您必須以具有系統管理權限的帳戶登入。 如需詳細資訊，請參閱[使用者權限和 Visual Studio](../ide/user-permissions-and-visual-studio.md)。

## <a name="modify-workloads"></a>修改工作負載

 [工作負載](https://visualstudio.microsoft.com/vs/visual-studio-workloads/)包含您使用的程式設計語言或平台所需功能。 您可以使用工作負載來修改 Visual Studio，以便在需要時支援您要執行的工作。

>[!NOTE]
> 下列程序假設您已具備網際網路連線。
>
> 如需如何修改先前所建立 Visual Studio [離線安裝](create-an-offline-installation-of-visual-studio.md)的詳細資訊，請參閱[更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)頁面和[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)頁面。

::: moniker range="vs-2017"

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行 Windows 10，的電腦上，選取 [開始]  ，然後捲動到字母 [V]  ，它在其中列為 [Visual Studio Installer]  。

     ![Visual Studio 安裝程式](media/vs2017-locate-the-visual-studio-installer.PNG "找出 Microsoft Visual Studio 安裝程式")

     >[!TIP]
     >在某些電腦上，Visual Studio 安裝程式可能會列在 **"M"** 字母下方，成為 [Microsoft Visual Studio 安裝程式]  。<br/><br/> 您也可以在下列位置找到 Visual Studio 安裝程式：`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 按一下或點選以啟動安裝程式，然後選擇 [修改]  。

     ![啟動或修改 Visual Studio](media/modify-visual-studio.png "修改 Visual Studio 2017")

     如果您有擱置的更新，則 [修改] 按鈕會在不同的位置。 因此，您可以修改而不需要更新 Visual Studio (如果您選擇這麼做)。 按一下 [更多]  ，然後選擇 [修改]  。

     ![更新或修改 Visual Studio](media/modify-or-update-visual-studio.png "更新或修改 Visual Studio 2017")

1. 從 [工作負載]  畫面，選取或取消選取您想要安裝或解除安裝的工作負載。

    ![Visual Studio 2017 安裝程式對話方塊](media/vs2017-modify-workloads.PNG "在 Visual Studio 2017 中選擇工作負載")

1. 再次選擇 [修改]  。

1. 新的工作負載和元件安裝之後，請選擇 [啟動]  。

::: moniker-end

::: moniker range="vs-2019"

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行 Windows 10，的電腦上，選取 [開始]  ，然後捲動到字母 [V]  ，它在其中列為 [Visual Studio Installer]  。

     ![從 Windows 開啟 Visual Studio 安裝程式](media/vs-2019/vs-installer-windows-start.png "開啟 Visual Studio 安裝程式")

     > [!NOTE]
     > 您也可以在下列位置找到 Visual Studio 安裝程式：
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    您可能需要更新安裝程式才能繼續。 若是如此，請遵循提示。

1. 請在安裝程式中尋找您安裝的 Visual Studio 版本，然後選擇 [修改]  。

     ![更新或修改 Visual Studio](media/vs-2019/vs-installer-modify.png "更新或修改 Visual Studio 2019")

1. 在 [工作負載]  索引標籤中，選取或取消選取您想要安裝或解除安裝的工作負載。

    ![Visual Studio 2019 安裝程式對話方塊](media/vs-2019/vs-installer-modify-workloads.png "在 Visual Studio 2019 中選擇工作負載")

1. 選擇接受預設的 [在下載時安裝]  選項還是 [全部下載後安裝]  選項。

    ![Visual Studio 2019 安裝選項](media/vs-2019/vs-installer-choose-install-or-download.png "選擇下載時安裝，或下載後再安裝")

    如果您想要下載後再安裝，則 [全部下載後安裝] 選項會很方便。

1. 選擇 [修改]  。

1. 安裝新的工作負載和元件後，請選擇 Visual Studio 安裝程式的 [啟動]  。

::: moniker-end

## <a name="modify-individual-components"></a>修改個別元件

如果您不想要安裝[工作負載](https://visualstudio.microsoft.com/vs/visual-studio-workloads/)來自訂 Visual Studio 安裝，請從 Visual Studio 安裝程式選擇 [個別元件]  索引標籤，選取所需的設定，然後遵循提示進行。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [深入了解 Visual Studio 工作負載](https://visualstudio.microsoft.com/vs/visual-studio-workloads/)
* [Visual Studio 工作負載與元件識別碼清單](workload-and-component-ids.md)
* [更新 Visual Studio](update-visual-studio.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
* [在維護基底上時更新 Visual Studio](update-servicing-baseline.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
