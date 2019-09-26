---
title: 設定 Visual Studio 容器工具
description: 設定 Visual Studio 中提供的工具，以使用 Docker 容器。
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: f05eb5d92c0cdaa1242f0d98c3d877eebae27bb1
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253165"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>如何設定 Visual Studio 容器工具

使用 Visual Studio 設定，您可以控制 Visual Studio 如何與 Docker 容器搭配運作的一些層面，包括在使用 Docker 容器時，會影響效能和資源使用量的設定。

## <a name="container-tools-settings"></a>容器工具設定

從主功能表中，選擇 [工具] > [選項]，並展開 [容器工具] > [設定]。 容器工具設定隨即出現。

::: moniker range="vs-2017"

![Visual Studio 容器工具選項，其中顯示：自動在專案載入時提取所需的 Docker 映像、自動在背景中啟動容器、自動在解決方案關閉時終止容器，以及不要提示信任 SSL 憑證。](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

容器工具**一般**設定：

![Visual Studio 容器工具選項，其中顯示：視需要安裝 Docker Desktop，並信任 ASP.NET Core SSL 憑證。](./media/configure-container-tools/tools-options-1.png)

容器工具**單一專案**和**Docker Compose**設定：

![Visual Studio 容器工具選項，其中顯示：在專案關閉時終止容器，在專案開啟時提取所需的 Docker 映射，並在專案開啟時執行容器。](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

下表可協助您決定如何設定這些選項。

::: moniker range="vs-2017"
| 名稱 | 預設設定 | 適用於 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 自動在專案載入時提取所需的 Docker 映像 | 開啟 | Docker Compose | 為了提高載入專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，因此當您準備好要執行程式碼時，映像已下載或正在下載中。 如果您只要載入專案並瀏覽程式碼，則可以關閉這項功能，避免下載您不需要的容器映像。 |
| 自動在背景中啟動容器 | 開啟 | Docker Compose | 同樣為了提高效能，Visual Studio 會在您建置並執行容器時建立一個容器，內含準備好可供使用的磁碟區裝載。 如果您想要控制何時建立容器，請關閉這項功能。 |
| 自動在解決方案關閉時終止容器 | 開啟 | Docker Compose | 如果您希望解決方案的容器在關閉解決方案或關閉 Visual Studio 之後繼續執行，請關閉這項功能。 |
| 不要提示信任 localhost SSL 憑證 | Off | ASP.NET Core 2.1 專案 | 如果 localhost SSL 憑證不受信任，則除非核取此核取方塊，否則每次執行專案時 Visual Studio 都會提示。 |
::: moniker-end

::: moniker range=">=vs-2019"

下表描述**一般**設定：

| 名稱 | 預設設定 | 適用於 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 視需要安裝 Docker Desktop | 提示我 | 單一專案，Docker Compose | 選擇是否要在未安裝 Docker Desktop 時提示您。 |
| 信任 ASP.NET Core SSL 憑證 | 提示我 | ASP.NET Core 2.x 專案 | 當設定為 [**提示我**] 時，如果 localhost SSL 憑證不受信任，則每次您執行專案時，Visual Studio 都會出現提示。 |

下表描述**單一專案**和**Docker Compose**設定：

| 名稱 | 預設設定 | 適用於 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 在專案開啟時提取所需的 Docker 映射 | True | 單一專案，Docker Compose | 為了提高載入專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，因此當您準備好要執行程式碼時，映像已下載或正在下載中。 如果您只是要載入專案和流覽程式碼，您可以將設定為**False** ，以避免下載不需要的容器映射。 |
| 在專案開啟時執行容器 | True | 單一專案，Docker Compose | 同樣地，為了提高效能，Visual Studio 會在一段時間後建立容器，以便在您建立和執行容器時準備就緒。 如果您想要控制建立容器的時間，請將設定為**False**。 |
| 在專案關閉時停止容器 | True | 單一專案和 Docker Compose | 如果您想要讓解決方案的容器在關閉解決方案或關閉 Visual Studio 之後繼續執行，請將設定為**False** 。 |

::: moniker-end
> [!WARNING]
> 如果 localhost SSL 憑證不受信任，且您核取 [隱藏提示] 方塊，則 HTTPS web 要求可能會在執行時間于您的應用程式或服務中失敗。 在此情況下，請取消核取 [不要提示] 核取方塊，執行您的專案，並在提示時表示信任。

## <a name="next-steps"></a>後續步驟

如需使用容器的詳細資訊，請參閱本[總覽](visual-studio-tools-for-docker.md)中的 Visual Studio。