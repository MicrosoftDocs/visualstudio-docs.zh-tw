---
title: "將部署到本機資料夾-Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e575a6d885b079c1c5afd0af6cbdadcd1d38d96
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>將 web 應用程式或.NET Core 應用程式部署至本機資料夾，使用 Visual Studio 發行工具

您可以使用**發行**工具，以將您的應用程式發行至本機資料夾。 

這些步驟適用於 ASP.NET、 ASP.NET Core、.NET Core 和 Visual Studio 的 Python 應用程式。 For Node.js，所支援的步驟，但是使用者介面不同。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

1. 在下**Visual C#**或**Visual Basic**，選擇**.NET Core**，然後在中間窗格選擇**主控台應用程式 (.NET Core)**。

1. 輸入的名稱，例如**MyLocalApp**按一下**確定**。

    Visual Studio 會建立專案。

## <a name="deploy-to-a-local-folder"></a>將部署到本機資料夾

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。

    ![選擇發行](../deployment/media/quickstart-publish.png "選擇發行")

1. 在**發行** 窗格中，選擇**資料夾**。

    ![選擇資料夾](../deployment/media/quickstart-publish-folder.png "選擇資料夾")

1. 輸入路徑，或按一下**瀏覽**瀏覽至本機資料夾。

1. 按一下 [發行] 。

    Visual Studio 建置專案，並將其發佈至指定的資料夾。

    [發行] 窗格會顯示摘要的設定檔。

1. 若要設定部署設定，請按一下**設定**摘要的設定檔中。

    ![設定檔設定](../deployment/media/quickstart-profile-settings.png "設定檔設定") 

1. 設定選項，例如是否要部署的偵錯或發行組態，然後按**儲存**。

1. 若要重新發佈，請按一下**發行**。

請使用任何您想要的方式，部署已發行的檔案。 比方說，您可以加以封裝 Zip 檔案中，使用簡單的複製命令，或將其部署與您所選擇的任何安裝套件。

## <a name="next-steps"></a>後續步驟

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs)
- [為 Microsoft Store (傳統型橋接器) 封裝傳統型應用程式](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET)[部署.NET Framework 和應用程式](/dotnet/framework/deployment/)
