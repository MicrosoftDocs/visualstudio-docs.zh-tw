---
title: 存取 Azure 私人雲端使用 Visual Studio |Microsoft Docs
description: 了解如何使用 Visual Studio 存取私人雲端資源。
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002021"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>存取 Azure 私人雲端使用 Visual Studio

根據預設，Visual Studio 支援 Azure 雲端 REST 端點。 在本文中，您會學習如何使用私人雲端的憑證來存取和使用 Visual Studio 的私人雲端。

1. 在私人雲端的 Azure 入口網站，下載發佈設定檔，或連絡您的系統管理員取得發行設定檔。 (檔案具有副檔名`.publishsettings`。)

1. 在 Visual Studio**伺服器總管**，以滑鼠右鍵按一下**Azure**節點，然後選取**管理及篩選訂閱**。

    ![管理訂用帳戶命令](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. 在 **管理的 Microsoft Azure 訂用帳戶**對話方塊中，選取**憑證**索引標籤，然後選取**匯入**。

    ![匯入 Azure 的憑證](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. 在 **匯入 Microsoft Azure 訂用帳戶**對話方塊中，選取**瀏覽**。

    ![瀏覽按鈕，在 [匯入 Microsoft Azure 訂用帳戶] 對話方塊](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. 在 [**開放**] 對話方塊中，瀏覽至您儲存發佈設定檔中，選取檔案，然後選取**開啟**。

    ![選取 發佈設定檔](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. 若要在傳回時**匯入 Microsoft Azure 訂用帳戶**對話方塊中，選取**匯入**。

    ![匯入發佈設定檔](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    憑證從 publish-settings 檔案匯入 Visual Studio 中，您現在可以與您的私用雲端資源互動。

