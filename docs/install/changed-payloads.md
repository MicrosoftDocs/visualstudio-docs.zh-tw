---
title: 套件承載在發行後變更的時間
description: 建立版面配置時，了解如何判斷套件承載是否在推出版本之後變更。
ms.date: 05/22/2019
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bd0013df051def28c57552c0aeb733888d55e9b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905545"
---
# <a name="package-payload-changes"></a>套件承載變更

有些套件承載可以在推出版本之後變更。 當您或某個人建立版面配置時，這種行為可能會導致不同的版面配置內容，端視建立版面配置的時間而定。

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>請確認版面配置包含套件承載變更

以下是如何判斷先前建立的版面配置是否已取得版本推出之後修改的套件承載：

1. 開啟安裝記錄檔。 此記錄檔通常在 `%TEMP%\dd_setup_[date].log`，其中 `[date]` 是版面配置作業啟動的時間 (`yyyyMMddHHmmss` 格式)。

2. 在記錄檔中尋找結構類似下列文字的那一行：

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. 然後，在之後的記錄檔中尋找指出 [path] 下載成功的那幾行。 這幾行看起來可能類似下列文字：

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>另請參閱

* [建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
