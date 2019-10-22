---
title: 部署圖層模型擴充功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669868"
---
# <a name="deploy-a-layer-model-extension"></a>部署圖層模型擴充功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

其他 Visual Studio 使用者可以安裝您使用 Visual Studio 建立的圖層模型擴充功能。

## <a name="installing-your-extension"></a>安裝您的擴充功能
 您的擴充功能會編譯成 VSIX 檔案，讓您安裝到其他電腦。 您也可以把擴充功能安裝在開發電腦，在 Visual Studio 的主要執行個體中使用它。

#### <a name="to-install-the-extension"></a>安裝擴充功能

1. 在包含 **.vsix**的專案中，在檔案瀏覽器中開啟**bin \\ \\** *。

2. 將 **\* .vsix**檔案複製到您要安裝擴充功能的電腦上。

3. 在目標電腦的 Windows [檔案總管] 中，按兩下 *.vsix 檔案。

    隨即開啟 VSIX 安裝程式。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1. 在 Visual Studio 的 [**工具**] 功能表上，按一下 [**擴充功能和更新**]。

2. 按一下延伸模組的名稱，然後按一下 [**卸載**]。

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>在 Team Foundation Build Server 上安裝擴充功能
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 伺服器通常沒有安裝 Visual Studio，因此無法按兩下就安裝 VSIX。 安裝 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 需有讓 VSIX 擴充功能執行的一些元件，但是這個擴充功能必須手動安裝。

#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>在 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 伺服器上安裝圖層擴充功能

1. 從您的開發電腦將 **.vsix**檔案複製到 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 的電腦。

     將 VSIX 檔案放在下列一個位置：

    - 為所有的使用者和服務安裝：

         %ProgramFiles%\Microsoft Visual Studio [版本]\Common7\IDE\Extensions\Microsoft

    - 只針對執行 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 的網路服務安裝：

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [版本] \Extensions\Microsoft

    - 如已設定 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 以特定使用者身分在互動模式中執行，可以只針對該使用者安裝：

         %LocalAppData%\Microsoft\VisualStudio \\ [版本] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData% 通常是*DriveName*： Users 使用者*名稱*AppDataLocal。

2. 在相同位置的資料夾中展開每個 VSIX 檔案：

    1. 將副檔名從 **.vsix**變更為 **.zip**。

    2. 將 .zip 檔案的內容解壓縮到資料夾。

    3. 刪除 .zip 檔案

3. 重新啟動 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]。
