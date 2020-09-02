---
title: 在本機電腦上使用 Emulator Express 來執行 Azure 雲端服務或對其進行偵錯
description: 使用 Emulator Express 在本機電腦上執行及偵錯雲端服務
author: mikejo5000
manager: jillfra
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: 0a6bbf5c846007cb1fa8d8cad91aa252f3d06a72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800368"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>使用 Emulator Express 在本機電腦上執行 Azure 雲端服務及對其進行偵錯
使用 Emulator Express，您可以測試及偵錯雲端服務，而不需以系統管理員身分執行 Visual Studio。 視您的雲端服務的需求而定，您可以進行專案設定以使用 Emulator Express 或完整模擬器。 如需完整模擬器的詳細資訊，請參閱 [在計算模擬器中執行 Azure 應用程式](/azure/storage/common/storage-use-emulator)。

## <a name="using-emulator-express-in-visual-studio"></a>在 Visual Studio 中使用 Emulator Express
當您在 Azure SDK 2.3 或更新版本中建立 Azure 專案時，會自動使用 Emulator Express。 對於使用舊版 Azure SDK 建立的現有專案，請使用下列步驟來選取 Emulator Express：

1. 在 Visual Studio 中建立或開啟 Azure 雲端服務專案。

1. 在方案總管中，以滑鼠右鍵按一下專案，然後從內容功能表中選取 [ **屬性**]。

1. 在專案屬性頁面中，選取 [Web]**** 索引標籤。

    ![Azure 雲端服務專案的屬性](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. 在 [本機程式開發伺服器]**** 之下，選取 [使用 IIS Express]**** 選項。

1. 在 [模擬器]**** 之下，選取 [使用 Emulator Express]****。

1. 若要啟動 Emulator Express，請在命令提示字元中執行下列命令：

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express 限制
下列問題是已知的 Emulator Express 限制：

- Emulator Express 與「IIS Web 伺服器」不相容。
- 您的雲端服務可以包含多個角色，但每個角色受限於一個執行個體。
- 您無法存取低於 1000 的連接埠號碼。 如果您使用的驗證提供者通常使用小於 1000 的連接埠，您可能需要將此值變更為大於 1000 的連接埠號碼。
- 任何適用於 Azure 計算模擬器的限制也適用於 Emulator Express。 例如，每一個部署不能有 50 個以上的角色執行個體。 如需有關「Azure 計算模擬器」的詳細資訊，請參閱[在計算模擬器中執行 Azure 應用程式](vs-azure-tools-performance-profiling-cloud-services.md)。

## <a name="next-steps"></a>後續步驟
[進行 Azure 雲端服務的偵錯](vs-azure-tools-debugging-cloud-services-overview.md)
