---
title: 如何：在套用 Visual Basic 開發者設定的情況下管理組建組態
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987419e62d54b44a21a70f625e2a240bd7aecc21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946256"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>如何：在套用 Visual Basic 開發者設定的情況下管理組建組態

根據預設，所有進階組建組態選項會隱藏，並套用 Visual Basic 開發人員設定。 本主題說明如何手動啟用這些設定。

## <a name="enable-advanced-build-configurations"></a>啟用進階組建組態

根據預設，Visual Basic 開發人員設定會隱藏開啟 [組態管理員] 對話方塊和[專案設計工具](..//ide/reference/application-page-project-designer-visual-basic.md)中的 [組態] 和 [平台] 清單的選項。

1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。

2.  展開 [專案和方案]，然後按一下 [一般]。

    > [!NOTE]
    > 即使未核取 [顯示所有設定] 選項，都可以看到 [一般] 節點。 如果您想要查看每個可用的選項，請按一下 [顯示所有設定]。

3.  按一下 [顯示進階組建組態]。

4.  按一下 [確定 **Deploying Office Solutions**]。

     在 [組建] 功能表上，現在已可使用 [組態管理員]，而且 [組態] 和 [平台] 清單也會顯示在**專案設計工具**中。

## <a name="see-also"></a>另請參閱

- [了解建置組態](../ide/understanding-build-configurations.md)
- [編譯及建置](../ide/compiling-and-building-in-visual-studio.md)