---
title: 管理 VS 包 |微軟文件
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
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702645"
---
# <a name="manage-vspackages"></a>管理 VSPackages
在大多數情況下,您不必擔心管理 VSPackage,因為專案和專案範本會自動註冊和載入套件。 但是,在某些情況下,您可能需要學習更多,以便管理您的包。

## <a name="use-the-experimental-instance"></a>使用實驗實例
 要瞭解有關實驗實例的更多,請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

## <a name="register-and-unregister-vspackages"></a>註冊與取消註冊 VS 套件
 要瞭解如何註冊和取消註冊 VS 包和其他類型的擴展,請參閱[註冊和取消註冊 VS 套件](../extensibility/registering-and-unregistering-vspackages.md)。

## <a name="load-a-vspackage"></a>載入 VS 套件
 VSPackages 可以設置為打開特定 CMDUICONTEXT GUID 時自動載入。 有關詳細資訊,請參閱載[入 VS 套件](../extensibility/loading-vspackages.md)。

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>使用非同步套件在背景中載入 VS 套件
 該`AsyncPackage`類允許在後台線程上載入包,從而在 Visual Studio 中實現更好的 UI 回應。 有關詳細資訊,請參閱[:使用非同步包在後台載入 VS 套件](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。

## <a name="rule-based-ui-context-for-extensions"></a>擴充的基於規則的 UI 功能
 基於規則的 UI 上下文允許擴充作者定義使用 UI 上下文並載入關聯的 VS 包的確切條件。 有關詳細資訊,請參閱[操作操作:對可視化工作室擴展使用基於規則的 UI 上下文](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。

## <a name="diagnose-extension-performance"></a>診斷延伸模組的效能
擴展可能會影響啟動和解決方案載入性能。 瞭解如何計算 Visual Studio 擴充影響,以及如何在本地對其進行分析,以測試擴展是否可以顯示為影響擴展的性能。 有關詳細資訊,請參閱[如何:診斷擴展性能](how-to-diagnose-extension-performance.md)。

## <a name="troubleshoot-vspackages"></a>排除 VS 套件容錯
 瞭解對未載入或遇到錯誤的 VS 套件進行故障排除的技術:[對 VSPackages 進行故障排除](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
