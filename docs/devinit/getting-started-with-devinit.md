---
title: 使用 devinit 開始使用
description: Devinit 的使用者入門指南。
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 99daeeff40091bb3600b82b1f25cc9cf44c52cf9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848236"
---
# <a name="getting-started-with-devinit"></a>使用 devinit 開始使用

devinit 是一種工具，您可以藉由執行簡單的命令，讓任何人都能取得程式碼，並在您的存放庫中提高生產力。 您可以使用 devinit 來定義存放庫所需的所有全系統相依性，例如 SQL server、Node.js、Docker 或 IIS。 Devinit 可以叫用其他工具和套件管理員，以安裝您的存放庫所需的內容。 您可以在名為 [.devinit.js](devinit-json.md) 的 JSON 檔案中定義這些相依性，然後使用您的存放庫的下一個人必須執行 [`devinit init`](devinit-commands.md#init) ，才能安裝所有這些相依性。 因此，您可以在短短幾分鐘內完成這項工作，而不需要花上半天的時間登入新的存放庫。

devinit 不是套件管理員或虛擬機器 (VM) configuration tool 本身。 它是名為 [.devinit.js](devinit-json.md)的資訊清單檔的工作執行器，它會定義您的應用程式所需的全系統相依性。 若要安裝這些相依性，devinit 會使用您可能已在使用的工具，例如 [Chocolatey](https://chocolatey.org)。 您可以在 [完整清單](devinit-tool-list.md)中查看可用的工具。 Devinit 藉由使用這些工具而不是直接散發軟體，讓您可以使用您選擇的工具，並讓您使用現有的設定，例如，用於 Chocolatey 的 [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) 檔案。  

## <a name="step-1-get-devinit"></a>步驟1：取得 devinit

devinit 目前僅在使用 Visual Studio 時可作為 GitHub Codespaces 的一部分，而且可從 Visual Studio 中的整合式終端機存取。 在未來，devinit 將可作為 Visual Studio 的一部分。

## <a name="step-2-define-your-environment"></a>步驟2：定義您的環境

最重要的步驟是在檔案的 [.devinit.js](devinit-json.md)中定義您的「開發」環境。 當您執行時，devinit 會使用此檔案來建立您的環境 `devinit init` 。

在此步驟中，請考慮您要讓某人啟動並執行專案儲存機制的指示。 例如，他們是否需要安裝 SQL？ 特定版本的 .NET Core？ 依此類推。 然後針對每個相依性，在 [工具清單](devinit-tool-list.md) 中尋找對應的 devinit 工具，並將其新增至存放庫的檔案 `.devinit.json` 。

您也可以在 [範例檔](sample-readme.md)中查看一系列的範例，或查看 [教學](tutorial.md)課程。

## <a name="step-3-enjoy"></a>步驟3：享受！

現在，所有人都必須在複製存放庫之後執行 `devinit init` 。

```console
devinit init
```

如果您使用的是 [GitHub Codespaces](https://github.com/features/codespaces)，您可以將設定為在布 `devinit init` 建 codespace 時自動執行。 若要深入瞭解，請參閱 [devinit 和 GitHub Codespaces 檔](devinit-and-codespaces.md)。
