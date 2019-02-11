---
title: 使用 Visual Basic 開發人員設定管理組建設定
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- advanced build configurations
- building with Visual Basic developer settings (Visual Studio)
- debug builds
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92ff0f0d79657855667c260754bbc4a9857fec83
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985847"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>作法：在套用 Visual Basic 開發人員設定的情況下管理組建組態

根據預設，在套用 Visual Basic 開發人員設定時，所有進階組建組態選項都會被隱藏。 本文說明如何手動啟用這些組建設定。

## <a name="enable-advanced-build-configurations"></a>啟用進階組建組態

根據預設，Visual Basic 開發人員設定會隱藏開啟 [組態管理員] 對話方塊和[專案設計工具](../ide/reference/application-page-project-designer-visual-basic.md)中的 [組態] 和 [平台] 清單的選項。

1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。

2.  展開 [專案和方案]，然後按一下 [一般]。

    > [!NOTE]
    > 即使未核取 [顯示所有設定] 選項，都可以看到 [一般] 節點。 如果您想要查看每個可用的選項，請按一下 [顯示所有設定]。

3.  按一下 [顯示進階組建組態]。

4.  按一下 [確定 **Deploying Office Solutions**]。

     在 [組建] 功能表上現在已可使用 [組態管理員]，且 [組態] 和 [平台] 清單也會顯示在 [專案設計工具] 中。

## <a name="see-also"></a>另請參閱

- [了解建置組態](../ide/understanding-build-configurations.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [環境設定](../ide/environment-settings.md)