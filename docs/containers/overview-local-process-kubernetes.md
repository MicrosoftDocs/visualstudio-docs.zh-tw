---
title: 本機處理序與 Kubernetes 搭配使用的方式
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: 描述搭配 Kubernetes 使用本機進程，將您的開發電腦連接到您的 Kubernetes 叢集的進程
keywords: 使用 Kubernetes、Docker、Kubernetes、Azure、容器的本機進程
monikerRange: '>=vs-2019'
ms.openlocfilehash: adde9d8ecab93bdb6f0aebbd74730ef60bd80cf6
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454305"
---
# <a name="how-local-process-with-kubernetes-works"></a>本機處理序與 Kubernetes 搭配使用的方式

使用 Kubernetes 的本機程式可讓您在開發電腦上執行和偵錯工具代碼，同時繼續與您的應用程式或服務的其餘部分連線到您的 Kubernetes 叢集。 例如，如果您有一個大型的微服務架構，其中包含許多互相相依的服務與資料庫，則在開發電腦上複寫這些相依性可能會很棘手。 此外，在內部迴圈開發期間，針對每個程式碼變更建立程式碼並將其部署到您的 Kubernetes 叢集，可能會很慢、耗時，而且很容易與偵錯工具搭配使用。

透過 Kubernetes 的本機程式可避免在您的開發電腦與叢集之間直接建立連線，而必須建立程式碼並將其部署到您的叢集。 在進行偵錯工具時，將您的開發電腦連接到叢集，可讓您在完整應用程式的內容中快速測試和開發服務，而不需要建立任何 Docker 或 Kubernetes 設定。

具有 Kubernetes 的本機進程會重新導向已連線的 Kubernetes 叢集與您的開發電腦之間的流量。 此流量重新導向可讓您的開發電腦上執行的程式碼與 Kubernetes 叢集中執行的服務進行通訊，就好像它們位於相同的 Kubernetes 叢集中一樣。 使用 Kubernetes 的本機進程也會提供一種方法，將環境變數和掛接的磁片區複寫至您的開發電腦中 Kubernetes 叢集中的 pod。 在您的開發電腦上提供環境變數和裝載的磁片區存取，可讓您快速處理常式代碼，而不需要手動複寫這些相依性。

## <a name="using-local-process-with-kubernetes"></a>搭配 Kubernetes 使用本機進程

若要在 Visual Studio 中使用本機進程與 Kubernetes，您需要[Visual Studio 2019][visual-studio] 16.7 Preview 4 版或更新版本，且已安裝*ASP.NET 和 網頁程式開發*工作負載，且已安裝[本機進程 Kubernetes 擴充][lpk-extension]功能。 當您使用本機進程搭配 Kubernetes 來建立 Kubernetes 叢集的連線時，您可以選擇將叢集中現有 pod 的所有流量重新導向至您的開發電腦。

> [!NOTE]
> 搭配 Kubernetes 使用本機進程時，系統會提示您輸入服務名稱，以重新導向至您的開發電腦。 此選項是識別重新導向之 pod 的便利方式。 Kubernetes 叢集與開發電腦之間的所有重新導向都適用于 pod。

當具有 Kubernetes 的本機進程建立與您叢集的連線時，它會：

* 提示您設定服務以取代您的叢集、開發電腦上要用於程式碼的埠，以及程式碼的啟動工作做為一次性動作。
* 使用將流量重新導向至您的開發電腦的遠端代理程式容器，取代叢集中 pod 中的容器。
* 在您的開發電腦上執行[kubectl 埠轉送][kubectl-port-forward]，以將流量從您的開發電腦轉送到叢集中正在執行的遠端代理程式。
* 使用遠端代理程式，從您的叢集收集環境資訊。 此環境資訊包括環境變數、可見服務、磁片區掛接和密碼裝載。
* 在 Visual Studio 中設定環境，讓開發電腦上的服務可以存取與在叢集上執行相同的變數。  
* 更新您的 hosts 檔案，將叢集上的服務對應至開發電腦上的本機 IP 位址。 這些裝載的檔案專案允許在您的開發電腦上執行的程式碼，對在您的叢集中執行的其他服務提出要求。 若要更新您的主機檔案，使用 Kubernetes 的本機進程會在連線到您的叢集時，要求您的開發電腦上的系統管理員存取權。
* 開始在您的開發電腦上執行和偵錯工具代碼。 如有必要，使用 Kubernetes 的本機進程將會停止目前正在使用這些埠的服務或處理常式，以在您的開發電腦上釋放所需的埠。

建立與叢集的連線之後，您可以在電腦上以原生方式執行和偵錯工具代碼，而不需要容器化，而且程式碼可以直接與叢集的其餘部分互動。 遠端代理程式接收的任何網路流量都會重新導向至連線期間指定的本機埠，讓您的原生執行程式碼可以接受並處理該流量。 您的叢集環境變數、磁片區和密碼可供在開發電腦上執行的程式碼使用。 此外，由於透過 Kubernetes 的本機程式，將主機檔案專案和埠轉送新增至您的開發人員電腦，因此您的程式碼可以使用叢集的服務名稱，將網路流量傳送至叢集上執行的服務，並將流量轉送到叢集中正在執行的服務。 您的開發電腦與叢集之間的流量會在您連線的整個時間進行路由。

## <a name="diagnostics-and-logging"></a>診斷和記錄

使用本機進程搭配 Kubernetes 來連線到您的叢集時，叢集的診斷記錄會記錄到開發電腦的[臨時目錄][azds-tmp-dir]中。

## <a name="limitations"></a>限制

具有 Kubernetes 的本機進程具有下列限制：

* 具有 Kubernetes 的本機進程會將單一服務的流量重新導向至您的開發電腦。 您無法搭配 Kubernetes 使用本機進程，同時重新導向多個服務。
* 服務必須由單一 pod 支援，才能連接到該服務。 您無法連接到具有多個 pod 的服務，例如具有複本的服務。
* Pod 在該 pod 中只能有一個執行的單一容器，可讓 Kubernetes 的本機進程成功連接。 具有 Kubernetes 的本機進程無法連接到具有其他容器之 pod 的服務，例如服務網格所插入的側車容器。
* 具有 Kubernetes 的本機進程需要較高的許可權，才能在您的開發電腦上執行，以編輯您的主機檔案。

## <a name="next-steps"></a>後續步驟

若要開始搭配 Kubernetes 使用本機進程來連接到您的本機開發電腦，請參閱搭配[Kubernetes 使用本機進程](local-process-kubernetes.md)。

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro