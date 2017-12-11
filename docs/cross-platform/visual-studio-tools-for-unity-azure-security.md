---
title: "Visual Studio Tools for Unity Azure 逐步解說安全性 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: d036d180fddcce443debe3d7917415380187994c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>更新 Unity Mono 安全性憑證存放區

Unity Mono 隨附空白憑證存放區，因此不信任任何網站。 如需詳細資訊，請參閱 [Mono 安全性常見問題集](http://www.mono-project.com/docs/faq/security/)。

為了連線到 Azure 而不需要略過 TLS / SSL，必須更新 Unity Mono 憑證存放區。

## <a name="using-mozroots-to-install-certificates"></a>使用 mozroots 安裝憑證

mozroots 工具隨附於 Mono。 它會下載並安裝 Mozilla 的根憑證清單。

1. 開啟命令提示字元終端機。

2. 在終端機中，巡覽至 **C:\Program Files\Unity\Editor\Data\MonoBleedingEdge\bin>** 目錄。 確切位置可能會因您在本機電腦上安裝 Unity 的位置而有所不同。

3. 鍵入下列命令，然後按 **Enter** 鍵加以執行：

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. 您應該取得下列輸出 (但新增的憑證數目可能不同)：

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. 現在您應該能夠執行範例專案，而不會收到 TLS 的相關錯誤。

## <a name="next-step"></a>後續步驟

* [測試用戶端連線](visual-studio-tools-for-unity-azure-connection.md)
