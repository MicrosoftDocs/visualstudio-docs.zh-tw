---
title: 解除安裝 Windows Installer VSPackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ddb09668d3114c055ddac1e4fb677a46754f388
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344754"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>使用 Windows Installer 解除安裝 VSPackage
大部分的情況下，Windows 安裝程式也可以解除安裝 VSPackage 只藉由 「 復原 」 一樣安裝 VSPackage。 自訂動作所述[命令，必須是執行之後安裝](../../extensibility/internals/commands-that-must-be-run-after-installation.md)必須也解除安裝後執行。 Devenv.exe 呼叫發生之前進行安裝和解除安裝的 installfinalize 發生標準動作，因為 CustomAction 和 InstallExecuteSequence 資料表項目會提供這兩種情況。

> [!NOTE]
> 執行`devenv /setup`之後解除安裝 MSI 套件。

 一般而言，如果您加入自訂動作加入 Windows Installer 封裝時，您必須處理這些動作期間解除安裝和復原。 如果您加入自訂動作來自行註冊 VSPackage，比方說，您必須加入過取消註冊，自訂動作。

> [!NOTE]
> 您可針對使用者安裝 VSPackage，然後解除安裝的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用的整合。 您可以協助確定 VSPackage 的解除安裝可在該案例中藉由消除執行具有相依性的程式碼的自訂動作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="handling-launch-conditions-at-uninstall-time"></a>處理啟動條件，在解除安裝時間
 LaunchConditions 標準動作讀取資料列的 LaunchCondition 資料表來顯示錯誤訊息不符合條件。 啟動條件通常用來確保符合系統需求，，您通常可以跳解除安裝期間啟動條件，藉由新增條件，因為`NOT Installed`，LaunchCondition 資料表的 LaunchConditions 資料列。

 替代方式是將`OR Installed`啟動解除安裝期間不重要的條件。 這可確保條件在解除安裝期間一律為 true，且因此不會顯示啟動條件錯誤訊息。

> [!NOTE]
> `Installed` 是 Windows 安裝程式設定在偵測到 VSPackage，已經安裝在系統上的屬性。

## <a name="see-also"></a>另請參閱
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)