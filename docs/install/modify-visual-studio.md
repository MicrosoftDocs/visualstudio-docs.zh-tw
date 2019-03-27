---
title: 修改 Visual Studio 2017
titleSuffix: ''
description: 了解如何逐步修改 Visual Studio。
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 06/12/2018
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
ms.openlocfilehash: 14b80de86c39f9c6ca253434fa90b9f1a4839df2
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324892"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>透過新增或移除工作負載和元件來修改 Visual Studio

我們不僅讓您可以更輕鬆地將 Visual Studio 個人化以配合您要完成的工作，也讓您可以更輕鬆地自訂 Visual Studio。 若要這樣做，請啟動新的 Visual Studio 安裝程式並進行所需的變更。

方式如下：

## <a name="modify-workloads"></a>修改工作負載

 工作負載包含您使用之程式設計語言或平台所需的功能。 您可以使用工作負載來修改 Visual Studio，以便在需要時支援您要執行的工作。

>[!IMPORTANT]
>若要安裝、更新或修改 Visual Studio，您必須以具有系統管理權限的帳戶登入。 如需詳細資訊，請參閱[使用者權限和 Visual Studio](../ide/user-permissions-and-visual-studio.md)。

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行 Windows 10，的電腦上，選取 [開始]，然後捲動到字母 [V]，它在其中列為 [Visual Studio Installer]。

     ![Visual Studio 安裝程式](media/vs2017-locate-the-visual-studio-installer.PNG "找出 Microsoft Visual Studio 安裝程式")

     >[!NOTE]
     >在某些電腦上，Visual Studio 安裝程式可能會列在 **"M"** 字母下方，成為 [Microsoft Visual Studio 安裝程式]。<br/><br/> 您也可以在下列位置找到 Visual Studio 安裝程式：`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2. 按一下或點選以啟動安裝程式，然後選擇 [修改]。

     ![啟動或修改 Visual Studio](media/modify-visual-studio.png "修改 Visual Studio 2017")

     如果您有擱置的更新，則 [修改] 按鈕會在不同的位置。 因此，您可以修改而不需要更新 Visual Studio (如果您選擇這麼做)。 按一下 [更多]，然後選擇 [修改]。

     ![更新或修改 Visual Studio](media/modify-or-update-visual-studio.png "更新或修改 Visual Studio 2017")

3. 從 [工作負載] 畫面，選取或取消選取您想要安裝或解除安裝的工作負載。

    ![Visual Studio 2017 安裝程式對話方塊](media/vs2017-modify-workloads.PNG "在 Visual Studio 2017 中選擇工作負載")

4. 再次選擇 [修改]。

5. 新的工作負載和元件安裝之後，請選擇 [啟動]。

## <a name="modify-individual-components"></a>修改個別元件

如果您不打算使用好用的 [工作負載] 功能來自訂 Visual Studio 安裝，請從 Visual Studio 安裝程式選擇 [個別元件] 選項，選取所需的設定，然後依照提示進行。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio](update-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
