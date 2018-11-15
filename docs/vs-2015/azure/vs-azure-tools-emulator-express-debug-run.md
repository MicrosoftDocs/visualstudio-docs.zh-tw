---
title: 使用 Emulator Express 以執行和偵錯在本機電腦上的 Azure 雲端服務 |Microsoft Docs
description: 使用 Emulator Express 以執行和偵錯在本機電腦上的雲端服務
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001396"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>使用 Emulator Express 在本機電腦上執行 Azure 雲端服務並對其進行偵錯
藉由使用 Emulator Express，您可以測試和偵錯雲端服務，而不需要系統管理員身分執行 Visual Studio。 您可以設定您的專案設定為使用 Emulator Express 或完整模擬器，根據您的雲端服務的需求。 如需有關完整模擬器的詳細資訊，請參閱 <<c0> [ 計算模擬器中執行 Azure 應用程式](/azure/storage/common/storage-use-emulator)。

## <a name="using-emulator-express-in-visual-studio"></a>在 Visual Studio 中使用 Emulator Express
當您建立在 Azure SDK 2.3 或更新版本的 Azure 專案時，會自動使用 Emulator Express。 對於使用舊版 Azure SDK 所建立的現有專案，使用下列步驟來選取 Emulator Express:

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，並從操作功能表中，選取**屬性**。

1. 在 專案屬性 頁面中，選取**Web**  索引標籤。

    ![Azure 雲端服務專案的屬性](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. 底下**本機開發伺服器**，選取**使用 IIS Express 選項**。

1. 底下**模擬器**，選取**使用 Emulator Express**。
   
1. 若要啟動 Emulator Express，請在命令提示字元執行下列命令： 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express 限制
下列問題是已知 Emulator Express 的限制： 

- Emulator Express 與不相容的 IIS Web 伺服器。
- 您的雲端服務可以包含多個角色，但每個角色僅限於一個執行個體。
- 您無法存取低於 1000年的連接埠號碼。 如果您使用驗證提供者通常使用低於 1000年的連接埠，您可能需要將此值變更為高於 1000年的連接埠號碼。
- 適用於 Azure 計算模擬器中的所有限制也適都用於 Emulator Express。 例如，您不能有超過 50 個角色執行個體，每個部署。 如需有關 Azure 計算模擬器的詳細資訊，請參閱 <<c0> [ 計算模擬器中執行 Azure 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=623050)。

## <a name="next-steps"></a>後續步驟
[偵錯 Azure 雲端服務](https://msdn.microsoft.com/library/azure/ee405479.aspx)
