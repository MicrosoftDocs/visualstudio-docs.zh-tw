---
title: 存取私人 Azure 雲端
description: 了解如何使用 Visual Studio 存取私人雲端資源。
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 5c54cf131dc85420377cda222ff6f4400dbbc04b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844511"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>使用 Visual Studio 存取 Azure 私人雲端

根據預設，Visual Studio 支援 Azure 雲端 REST 端點。 在本文中，您將了解如何使用私人雲端的憑證，從 Visual Studio 存取私人雲端 (並進行互動)。

1. 在私人雲端的 Azure 入口網站中，下載發佈設定檔，或連絡您的系統管理員以取得發佈設定檔。 (檔案具有副檔名 `.publishsettings`。)

1. 在 Visual Studio [伺服器總管] 中，以滑鼠右鍵按一下 [Azure] 節點，然後選取 [管理及篩選訂閱]。

    ![管理訂用帳戶命令](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. 在 [管理 Microsoft Azure 訂用帳戶] 對話方塊中，選取 [憑證] 索引標籤，然後選取 [匯入]。

    ![正在匯入 Azure 憑證](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. 在 [匯入 Microsoft Azure 訂用帳戶] 對話方塊中，選取 [瀏覽]。

    ![[匯入 Microsoft Azure 訂用帳戶] 對話方塊上的 [瀏覽] 按鈕](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. 在 [開啟] 對話方塊中，瀏覽至您儲存發佈設定檔的目錄、選取檔案，然後選取 [開啟]。

    ![選取發佈設定檔](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. 當您返回 [匯入 Microsoft Azure 訂用帳戶] 對話方塊時，選取 [匯入]。

    ![匯入發佈設定檔](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    憑證會從發佈設定檔匯入 Visual Studio，而您現在可以與您的私人雲端資源互動。
