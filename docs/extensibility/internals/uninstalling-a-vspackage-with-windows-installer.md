---
title: 解除安裝 Windows Installer VSPackage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8a62692003b26afcd5b7814bdc03320fa1c453a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>解除安裝 Windows Installer VSPackage
大部分的情況下，Windows Installer 可以解除安裝 VSPackage 只由 「 復原 」 一樣安裝 VSPackage。 自訂動作所述[命令，必須是執行之後安裝](../../extensibility/internals/commands-that-must-be-run-after-installation.md)必須也解除安裝後執行。 因為 devenv.exe 呼叫 InstallFinalize 標準動作，進行安裝和解除安裝之前，CustomAction 和 InstallExecuteSequence 資料表項目會做這兩種情況。  
  
> [!NOTE]
>  執行`devenv /setup`MSI 套件解除安裝之後。  
  
 一般而言，如果您新增自訂動作加入 Windows Installer 封裝時，您必須處理這些動作期間解除安裝和復原。 如果您新增進行自助式註冊 VSPackage 的自訂動作，比方說，您必須將取消登錄該，過自訂動作。  
  
> [!NOTE]
>  它是使用者可以安裝 VSPackage，然後再解除安裝的版本可能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用的整合。 您可以協助確定 VSPackage 的解除安裝可在這個案例中藉由消除執行具有相依性的程式碼的自訂動作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>處理啟動條件，在解除安裝時間  
 LaunchConditions 標準動作讀取 LaunchCondition 資料表來顯示錯誤的資料列不符合條件時訊息。 啟動條件通常用來確保符合系統需求，您可以通常以略過啟動條件解除安裝期間加入條件， `NOT Installed`，LaunchCondition 資料表的 LaunchConditions 資料列。  
  
 替代方式是將`OR Installed`啟動解除安裝期間不重要的條件。 這可確保條件解除安裝期間永遠是 true，而且因此不會顯示啟動條件錯誤訊息。  
  
> [!NOTE]
>  `Installed` 這是當它偵測到您的 VSPackage 確認已安裝在系統上，設定 Windows Installer 屬性。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Installer](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)