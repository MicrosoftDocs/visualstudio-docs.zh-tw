---
title: 配置視覺化工作室容器工具
description: 配置 Visual Studio 中可用的工具，以便使用 Docker 容器。
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188782"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>如何配置視覺化工作室容器工具

使用 Visual Studio 設置，您可以控制 Visual Studio 如何使用 Docker 容器的某些方面，包括使用 Docker 容器時影響性能和資源使用方式的設置。

## <a name="container-tools-settings"></a>容器工具設置

從主功能表中，選擇 [工具] > [選項]****，並展開 [容器工具] > [設定]****。 容器工具設定隨即出現。

::: moniker range="vs-2017"

![Visual Studio 容器工具選項，顯示：在專案負載上自動拉取所需的 Docker 映射，在後臺自動啟動容器，在解決方案關閉時自動殺死容器，並且不提示信任 SSL 憑證。](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

容器工具**常規**設置：

![Visual Studio 容器工具選項，顯示：根據需要安裝 Docker 桌面，並信任ASP.NET核心 SSL 憑證。](./media/configure-container-tools/tools-options-1.png)

容器工具**單個專案和** **Docker 合成**設置：

![Visual Studio 容器工具選項，顯示：在專案關閉時殺死容器，在專案打開時拉動所需的 Docker 映射，在專案打開時運行容器。](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

下表可協助您決定如何設定這些選項。

::: moniker range="vs-2017"
| 名稱 | 預設值 | 套用至 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 自動在專案載入時提取所需的 Docker 映像 | 另一 | Docker Compose | 為了提高載入專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，因此當您準備好要執行程式碼時，映像已下載或正在下載中。 如果您只要載入專案並瀏覽程式碼，則可以關閉這項功能，避免下載您不需要的容器映像。 |
| 自動在背景中啟動容器 | 另一 | Docker Compose | 同樣為了提高效能，Visual Studio 會在您建置並執行容器時建立一個容器，內含準備好可供使用的磁碟區裝載。 如果您想要控制何時建立容器，請關閉這項功能。 |
| 自動在解決方案關閉時終止容器 | 另一 | Docker Compose | 如果您希望解決方案的容器在關閉解決方案或關閉 Visual Studio 之後繼續執行，請關閉這項功能。 |
| 不要提示信任 localhost SSL 憑證 | 關閉 | ASP.NET核心 2.1 專案 | 如果 localhost SSL 憑證不受信任，則除非核取此核取方塊，否則每次執行專案時 Visual Studio 都會提示。 |
::: moniker-end

::: moniker range=">=vs-2019"

下表描述了**常規**設置：

| 名稱 | 預設值 | 套用至 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 如果需要，安裝 Docker 桌面 | 提示我 | 單個專案，Docker 組合 | 如果未安裝 Docker 桌面，請選擇是否要提示您。 |
| 信任ASP.NET核心 SSL 憑證 | 提示我 | ASP.NET核心 2.x 專案 | 當設置為 **"提示我"** 時，如果本地主機 SSL 憑證不受信任，則每次運行專案時，Visual Studio 都會提示。 |

下表描述了**單個專案和**Docker**組合設置**：

| 名稱 | 預設值 | 套用至 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 在專案打開時拉動所需的 Docker 映射 | True | 單個專案，Docker 組合 | 為了提高載入專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，因此當您準備好要執行程式碼時，映像已下載或正在下載中。 如果您只是載入專案和流覽代碼，則可以設置為**False**以避免下載不需要的容器映射。 |
| 在專案打開時運行容器 | True | 單個專案，Docker 組合 | 為了提高性能，Visual Studio 會提前創建一個容器，以便在生成和運行容器時準備好。 如果要控制創建容器的創建時間，請設置為**False**。 |
| 專案關閉時停止容器 | True | 單個專案和 Docker 組合 | 如果您希望解決方案的容器在關閉解決方案或關閉 Visual Studio 後繼續運行，請設置為 **"False"。** |

::: moniker-end
> [!WARNING]
> 如果本地主機 SSL 憑證不受信任，並且選中此框以禁止提示，則 HTTPS Web 請求可能會在應用或服務中的運行時失敗。 在此情況下，請取消核取 [不要提示]**** 核取方塊，執行您的專案，並在提示時表示信任。

## <a name="next-steps"></a>後續步驟

在此概述中，閱讀有關使用 Visual Studio 中的容器[的詳細資訊](overview.md)。