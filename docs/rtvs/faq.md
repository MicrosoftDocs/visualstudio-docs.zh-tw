---
title: Visual Studio R 工具常見問題集
description: 在 Visual Studio 中有關 R 的常見問題。
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ecb64f12783b99cd0f26c59ee4ee298c5fabde72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885751"
---
# <a name="frequently-asked-questions"></a>常見問題集

## <a name="visual-studio-support"></a>Visual Studio 支援

**問。RTVS 適用于 OS X 或 Linux 嗎？**

A. RTVS 目前是以 Visual Studio 為基礎建置，而 Visual Studio 為僅限 Windows 的實作。 Microsoft 正在研究 Visual Studio Code 和 Visual Studio for Mac 的支援。 請參閱 [RTVS 問題 #1295](https://github.com/Microsoft/RTVS/issues/1295)。

**問。RTVS 是否適用于 Visual Studio Express 版？**

A. 否。

**問。我可以搭配使用 Visual Studio 擴充功能與 RTVS 嗎？**

A. 當然。 說到這個，以下是使用 R 的人員最愛使用的幾個擴充功能。

- [適用於 Vim 金鑰繫結的 VsVim (英文)](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [具有即時預覽的 Markdown 編輯器 (英文)](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

請造訪 [Visual Studio Marketplace (英文)](https://marketplace.visualstudio.com/) 以尋找更多擴充功能。

**問。因為 RTVS 是 Visual Studio，這表示 R 可以輕鬆地搭配 c #、c + + 及其他 Microsoft 語言使用？**

A. 否。 RTVS 是開發 R 程式碼的工具，並會使用標準的原生 R 解譯器。 目前不支援 R 與其他語言互通。

**問。RTVS 是否適用于非英文地區設定？**

A. RTVS 的 1.0 版僅支援英文。 1.1 版將會針對和 Visual Studio 本身相同的語言集進行當地語系化。 在此期間，請使用[適用於 Visual Studio 2015 的英文語言套件](https://www.microsoft.com/download/details.aspx?id=48157)。針對 Visual Studio 2017，請執行安裝程式，並在 [語言套件] 索引標籤中選取 [英文]。

![適用於 Visual Studio 2017 的國際設定](media/FAQ-international-settings.png)

**問。我很喜歡目前的 Visual Studio 設定，但是我想要嘗試新的資料科學設定。我該怎麼做？**

A. 使用 **工具** 匯  >  **入和匯出設定** 來儲存目前的 Visual Studio 設定，然後切換至資料科學設定。 若要還原已儲存的設定，請再次使用 [匯入和匯出設定] 命令。

**問。我可以將 Visual Studio 專案儲存在網路共用嗎？**

A. 否，Visual Studio 不支援從網路共用載入專案。

## <a name="r-interpretersintegration"></a>R 解譯器/整合

**問。RTVS 可搭配使用什麼 R 解譯器？**

A. [CRAN R](https://cran.r-project.org/)、[Microsoft R Client 及 Microsoft Machine Learning Server](/machine-learning-server/)

**問。我可以在哪裡下載這些解譯器？**

A. 請參閱[安裝](installing-r-tools-for-visual-studio.md)。

問：**什麼是 Microsoft R Server？**

A. R Server 是 [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server) 的舊稱。

**問。RTVS 是否適用于32位版本的 R？**

A. 否，RTVS 僅支援在 Windows 64 位元版本上執行之 R 的 64 位元版本。

**問。RTVS 是否可與我的原始檔控制系統搭配使用？**

A. 是，您可以使用任何與 Visual Studio 整合的原始檔控制系統。

**問。RTVS 專案的 *.gitignore* 設定是什麼？**

A. GitHub 會維護建議 *.gitignore* 檔案的存放庫。 您可以在此查看它：[R .gitignore (英文)](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>遠端服務

Q. **什麼是 Visual Studio 中的遠端服務？**

A. Visual Studio 的遠端 R 服務可讓您設定 Windows 或 Linux 電腦，並從 RTVS 連線到該服務。 請參閱[設定遠端工作區](setting-up-remote-r-workspaces.md)。

Q. **RTVS 可以連線到 Microsoft Machine Learning Server 嗎？**

A. 不可以，因為 Microsoft ML Server 是不同的技術，不會提供 RTVS 所需的相同連線機制。

Q. **RTVS 可以連線到使用 Azure 上的資料科學 VM 映像建立的 VM 嗎？**

A. 可以，[資料科學 VM - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) 映像以預先安裝的形式隨附於 Visual Studio 的遠端 R 服務。

問：**RTVS 可以連線到安裝 R 的遠端電腦嗎？**

若要在遠端電腦上執行 R 程式碼，必須有些服務接聽要求、接收程式碼，並將結果傳回用戶端電腦。 這就是 Visual Studio 的遠端 R 服務功能。 請參閱[設定遠端工作區](setting-up-remote-r-workspaces.md)。

Q. **什麼是遠端工作階段？**

A. 請參閱 Machine Learning Server 文件中的[在遠端伺服器上執行](/machine-learning-server/r/how-to-execute-code-remotely)一節。

## <a name="rtvs-development-and-features"></a>RTVS 開發和功能

**問：缺少功能 X，但 RStudio 有！**

A. 適用於 R 的 RStudio 是一個優秀且成熟的 IDE，且已經開發多年。 RTVS 正在努力包含所有您成功所需的重要功能。 在 [GitHub](https://github.com/Microsoft/RTVS/issues/)上提出問題，以協助設定未來工作的優先順序。

**問。我可以參與 RTVS 嗎？**

A. 當然！ 原始程式碼位於 [GitHub (英文)](https://github.com/microsoft/RTVS) 上。 使用問題追蹤器提交 Bug，以及對已歸檔的 Bug 提出註解。

也歡迎您參與編輯這份文件&mdash;，只要選取任一頁面右上角的 [編輯] 命令，即可開始編輯文件。 我們也歡迎您在文件上提出註解，您可以在任何頁面的底部加入註解。
