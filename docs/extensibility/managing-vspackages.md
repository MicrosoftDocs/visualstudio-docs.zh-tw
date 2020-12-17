---
title: 管理 Vspackage |Microsoft Docs
description: 瞭解如何管理 Vspackage，讓您知道何時可以直接使用 Visual Studio 所提供的預設 VSPackage 管理，以及如何和何時進行自訂。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a040777671a5d6a4378e9b2ad68b2ffa2fabaeb
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615736"
---
# <a name="manage-vspackages"></a>管理 VSPackages
在大多數情況下，您不需要擔心管理 Vspackage，因為專案和專案範本會自動註冊和載入封裝。 不過，在某些情況下，您可能需要更多的學習，才能管理您的封裝。

## <a name="use-the-experimental-instance"></a>使用實驗實例
 若要瞭解實驗實例的詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。

## <a name="register-and-unregister-vspackages"></a>註冊和取消註冊 Vspackage
 若要瞭解如何註冊及取消註冊 Vspackage 和其他類型的延伸模組，請參閱 [註冊和取消註冊 vspackage](../extensibility/registering-and-unregistering-vspackages.md)。

## <a name="load-a-vspackage"></a>載入 VSPackage
 當特定 CMDUICONTEXT GUID 開啟時，可以將 Vspackage 設定為自動載入。 如需詳細資訊，請參閱 [Load vspackage](../extensibility/loading-vspackages.md)。

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>在背景中使用 AsyncPackage 載入 Vspackage
 `AsyncPackage`類別可讓您在背景執行緒上載入封裝，以提升 Visual Studio 中的 UI 回應性。 如需詳細資訊，請參閱 [如何：在背景中使用 AsyncPackage 載入 vspackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。

## <a name="rule-based-ui-context-for-extensions"></a>延伸模組的以規則為基礎的 UI 內容
 以規則為基礎的 UI 內容，可讓延伸模組作者定義啟用 UI 內容並載入相關聯 Vspackage 的精確條件。 如需詳細資訊，請參閱 [如何：使用 Visual Studio 擴充功能的以規則為基礎的 UI 內容](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。

## <a name="diagnose-extension-performance"></a>診斷延伸模組的效能
擴充功能可能會影響啟動和解決方案載入效能。 瞭解如何計算 Visual Studio 擴充功能的影響，以及如何在本機進行分析以測試擴充功能是否會顯示為影響效能的擴充功能。 如需詳細資訊，請參閱 [如何：診斷延伸模組效能](how-to-diagnose-extension-performance.md)。

## <a name="troubleshoot-vspackages"></a>針對 Vspackage 進行疑難排解
 瞭解針對未載入或發生錯誤之 Vspackage 進行疑難排解的技術： [疑難排解 vspackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>另請參閱
- [VSPackages](../extensibility/internals/vspackages.md)
