---
title: 如何使用 kubectl 和已連線的環境 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>使用 `kubectl` 和已連線的環境

您可以在已連線的環境中存取 Kubernetes 叢集，並使用現有的 Kubernetes 工具，如 `kubectl`。

執行 `vsce env create` 或 `vsce env select` 會自動為您新增 `kubectl` 組態內容，所以 kubectl 應該已經連接到您的 VSCE Kubernetes 叢集。 例如：
- 確認目前的內容：`kubectl config current-context`
- 列出所有可用的內容：`kubectl config get-contexts`。 VSCE 所建立之 kubernetes 叢集的名稱會類似 "vsce-<guid>"。
- 變更內容：`kubectl config use-context <context-name>`
- 檢視 Kubernetes 儀表板：執行 `kubectl proxy`，然後在此命令發出的位址開啟您的瀏覽器 (將 `/ui` 附加至 URL，以巡覽至 Kubernetes 儀表板)。
- 列出在預設 VSCE 空間 *mainline* 中執行的服務：`kubectl get services --namespace=mainline`

