---
title: 使用 devinit 消費者入門
description: Devinit 的使用者入門指南。
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e0c6676b65637840a1b5878e06d6c5861c34e65d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809310"
---
# <a name="getting-started-with-devinit"></a>使用 devinit 消費者入門

## <a name="step-1-get-devinit"></a>步驟1：取得 devinit

devinit 目前僅在使用 Visual Studio 時可作為 GitHub Codespaces 的一部分，而且可從 Visual Studio 中的整合式終端機存取。 在未來，devinit 將可作為 Visual Studio 的一部分。

## <a name="step-2-define-your-environment"></a>步驟2：定義您的環境

最重要的步驟是在檔案的[ _.devinit.js_ ](devinit-json.md)中定義您的「開發人員」環境。 當您執行時，devinit 會使用此檔案來建立您的環境 `devinit init` 。

在此步驟中，請考慮您要讓某人啟動並執行專案儲存機制的指示。 例如，他們是否需要安裝 SQL？ 特定版本的 .NET Core？等。然後針對這些相依性，在 [工具清單](devinit-tool-list.md)) 中尋找對應的 devinit 工具，並將其新增至存放庫的 _.devinit.js_ 檔案。

## <a name="step-3-enjoy"></a>步驟3：享受！

現在，所有人都必須在複製存放庫之後執行 `devinit init` 。

```batch
> devinit init
```

如果您使用的是 [GitHub Codespaces](https://github.com/features/codespaces)，您可以將設定為在布 `devinit init` 建 codespace 時自動執行。 若要深入瞭解，請參閱 [devinit 和 GitHub Codespaces 檔](devinit-and-codespaces.md)。
