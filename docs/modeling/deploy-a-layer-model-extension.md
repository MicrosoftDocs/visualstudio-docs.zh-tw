---
title: 部署圖層模型擴充功能
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d44e5deaa9e631255d0a4f36d7b5f175b7d14611
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="deploy-a-layer-model-extension"></a>部署圖層模型擴充功能
其他 Visual Studio 使用者可以安裝您使用 Visual Studio 建立的圖層模型擴充功能。

## <a name="installing-your-extension"></a>安裝您的擴充功能
 您的擴充功能會編譯成 VSIX 檔案，讓您安裝到其他電腦。 您也可以把擴充功能安裝在開發電腦，在 Visual Studio 的主要執行個體中使用它。

#### <a name="to-install-the-extension"></a>安裝擴充功能

1.  包含專案中**source.vsix.manifest**，開啟**bin\\ \*** 檔案總管 中。

2.  複製 **\*.vsix**檔案至您要安裝擴充功能的電腦。

3.  在目標電腦的 Windows [檔案總管] 中，按兩下 *.vsix 檔案。

     隨即開啟 VSIX 安裝程式。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1.  在 Visual Studio 中，在**工具**功能表上，按一下 **擴充功能和更新**。

2.  按一下 延伸模組的名稱，然後按一下**解除安裝**。

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>在 Team Foundation Build Server 上安裝擴充功能
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 伺服器通常沒有安裝 Visual Studio，因此無法按兩下就安裝 VSIX。 安裝 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 需有讓 VSIX 擴充功能執行的一些元件，但是這個擴充功能必須手動安裝。

#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>在 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 伺服器上安裝圖層擴充功能

1.  複製 **.vsix**檔案從您的開發電腦[!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]電腦。

     將 VSIX 檔案放在下列一個位置：

    -   為所有的使用者和服務安裝：

         %ProgramFiles%\Microsoft Visual Studio [版本]\Common7\IDE\Extensions\Microsoft

    -   只針對執行 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 的網路服務安裝：

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   如已設定 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 以特定使用者身分在互動模式中執行，可以只針對該使用者安裝：

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

        > [!NOTE]
        >  %Localappdata%通常是*DriveName*： 使用者*UserName*AppDataLocal。

2.  在相同位置的資料夾中展開每個 VSIX 檔案：

    1.  變更檔案的副檔名從 **.vsix**至 **.zip**。

    2.  將 .zip 檔案的內容解壓縮到資料夾。

    3.  刪除 .zip 檔案

3.  重新啟動 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]。
