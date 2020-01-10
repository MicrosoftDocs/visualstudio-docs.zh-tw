---
title: 修復 Visual Studio
titleSuffix: ''
description: 了解如何修復 Visual Studio 2017 的安裝
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 255995f7ca660d36ae40a6a8fead4b3ea5d70424
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594548"
---
# <a name="repair-visual-studio"></a>修復 Visual Studio

::: moniker range="vs-2017"

有時您的 Visual Studio 安裝會損壞或損毀。 修復可以修正此問題。

1. 在您的電腦上找到 **Visual Studio 安裝程式**。

     例如，在執行「Windows 10 年度更新版」或更新版本的電腦上，選取 [開始]，然後捲動至字母 [V]，它是列為 [Visual Studio 安裝程式]。

   > [!NOTE]
   > 在某些電腦上，Visual Studio 安裝程式可能會列在 **"M"** 字母下方，成為 [Microsoft Visual Studio 安裝程式]。
   >
   > 您也可以在下列位置找到 Visual Studio 安裝程式：`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 開啟安裝程式，選擇 [更多]，然後選擇 [修復]。

    ![從 Visual Studio 安裝程式修復 Visual Studio](media/repair-visual-studio.png "從 Visual Studio 安裝程式修復 Visual Studio")

   > [!NOTE]
   > 修復 Visual Studio 會重設環境。 個別使用者沒有使用提高權限所安裝的擴充、使用者設定和設定檔等本機自訂項目會被移除。 佈景主題、色彩、按鍵繫結等已同步處理的設定會還原。
   >

   > [!TIP]
   > [修復] 選項僅會針對已安裝的 Visual Studio 執行個體加以顯示。 如果您看不到 [修復] 選項，很可能是您選取 [更多] 的版本在 Visual Studio 安裝程式中是列為「可用」而非「已安裝」。

::: moniker-end

::: moniker range="vs-2019"

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行 Windows 10，的電腦上，選取 [開始]，然後捲動到字母 [V]，它在其中列為 [Visual Studio Installer]。

     ![開啟 Visual Studio 安裝程式](media/vs-2019/vs-installer-windows-start.png "開啟 Visual Studio 安裝程式")

     > [!NOTE]
     > 您也可以在下列位置找到 Visual Studio 安裝程式：
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    您可能需要更新安裝程式才能繼續。 若是如此，請遵循提示。

1. 請在安裝程式中尋找您安裝的 Visual Studio 版本。 接著，選擇 [更多]，然後選擇 [修復]。

     ![修復 Visual Studio 2019](media/vs-2019/vs-installer-repair.png "修復 Visual Studio 2019")

   > [!NOTE]
   > 修復 Visual Studio 會重設環境。 個別使用者沒有使用提高權限所安裝的擴充、使用者設定和設定檔等本機自訂項目會被移除。 佈景主題、色彩、按鍵繫結等已同步處理的設定會還原。
   >

   > [!TIP]
   > [修復] 選項僅會針對已安裝的 Visual Studio 執行個體加以顯示。 如果您看不到 [修復] 選項，很可能是您選取 [更多] 的版本在 Visual Studio 安裝程式中是列為「可用」而非「已安裝」。

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio](update-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
* [針對 Visual Studio 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)
