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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 98697642135627173c5a6f31e90bf1dd1d0caeaf
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307748"
---
# <a name="deploy-a-layer-model-extension"></a>部署圖層模型擴充功能

其他 Visual Studio 使用者可以安裝您使用 Visual Studio 建立的圖層模型擴充功能。

## <a name="install-your-extension"></a>安裝擴充功能

您的擴充功能會編譯成 VSIX 檔案，讓您安裝到其他電腦。 您也可以把擴充功能安裝在開發電腦，在 Visual Studio 的主要執行個體中使用它。

### <a name="to-install-the-extension"></a>安裝擴充功能

1. 包含專案中**source.vsix.manifest**，開啟*bin*目錄檔案總管 中。

2. 複製 **\*.vsix**檔案至您要安裝擴充功能的電腦。

3. 在目標電腦的 Windows [檔案總管] 中，按兩下 *.vsix 檔案。

    隨即開啟 VSIX 安裝程式。

### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1.  在 Visual Studio 中，在**工具**功能表上，按一下**擴充功能和更新**。

2.  按一下 延伸模組的名稱，然後按一下**解除安裝**。

## <a name="install-an-extension-on-team-foundation-server"></a>Team Foundation Server 上安裝擴充功能

Team Foundation Server 伺服器通常沒有安裝 Visual Studio，並因此按兩下它無法安裝 VSIX。 您必須手動安裝擴充功能。

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>安裝 Team Foundation Server 伺服器上的圖層擴充功能

1.  複製。*vsix*檔案從您的開發電腦複製到 Team Foundation Server (TFS) 的電腦。

     將 VSIX 檔案放在下列一個位置：

    -   為所有的使用者和服務安裝：

         %ProgramFiles%\Microsoft Visual Studio [版本]\Common7\IDE\Extensions\Microsoft

    -   若要安裝僅針對執行組建的網路服務：

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   如果您已設定為特定使用者的互動模式中執行組建，您可以只針對該使用者進行安裝：

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

2.  在相同位置的資料夾中展開每個 VSIX 檔案：

    1.  變更從副檔名 **.vsix**要 **.zip**。

    2.  將 .zip 檔案的內容解壓縮到資料夾。

    3.  刪除 .zip 檔案

3.  重新啟動 TFS。
