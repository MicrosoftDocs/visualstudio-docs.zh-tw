---
title: Docker 教學課程-接下來
description: 描述使用雲端原生運算基礎專案來擴充 Docker 應用程式與協調流程的選項。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8ca68b2eba710037535b4bd76c744e7c029a53e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841649"
---
# <a name="whats-next"></a>後續步驟

雖然您已完成本教學課程，但仍有更多相關資訊可瞭解容器！
您將不會在此深入探討，但以下是其他幾個可供您參考的區域！

## <a name="container-orchestration"></a>容器協調流程

在生產環境中執行容器是很困難的。 您不想要登入電腦，只要執行 `docker run` 或 `docker-compose up` 。 為什麼不用？ 嗯，如果容器骰子，會發生什麼事？ 您如何在多部電腦之間進行調整？ 容器協調流程可解決此問題。 Kubernetes、Swarm、Nomad 和 AKS 等工具都能協助您解決這個問題，全都以稍微不同的方式來解決。

一般的概念是，您有「經理」會收到 **預期的狀態**。 此狀態可能是「我想要執行 web 應用程式的兩個實例，並公開端口80」。 管理員接著會查看叢集中的所有電腦，並將工作委派給「背景工作」節點。 管理員會監看 (之類的變更，例如，容器會結束) ，然後努力讓 **實際狀態** 反映預期的狀態。

## <a name="cloud-native-computing-foundation-projects"></a>雲端原生運算基礎專案

CNCF 是不同開放原始碼專案的廠商中立家用，包括 Kubernetes、Prometheus、Envoy、Linkerd、NAT 等等！ 您可以在此查看已 [分級和這是的專案](https://www.cncf.io/projects/) ，並在此查看整個 [CNCF 環境](https://landscape.cncf.io/)。 有許多專案可協助您解決有關監視、記錄、安全性、映射登錄、訊息和更多功能的問題！

如果您不熟悉容器的環境和雲端原生應用程式開發，歡迎您！ 請連接到該社區、提出問題，並持續學習！ 很高興有您！

## <a name="working-with-docker-in-vs-code"></a>在 VS Code 中使用 Docker

深入瞭解如何使用 VS Code Docker 延伸模組：

- [VS Code Docker 延伸模組總覽](https://code.visualstudio.com/docs/containers/overview)
- [開始使用 Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [開始使用 Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [.NET Core 使用者入門](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [偵錯工具容器化應用程式](https://code.visualstudio.com/docs/containers/debug-common)
