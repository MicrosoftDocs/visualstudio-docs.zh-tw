---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657912"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

通知 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 套件，並檢查 MEF 快取中的任何變更。

## <a name="syntax"></a>語法

```
devenv /updateconfiguration
```

## <a name="remarks"></a>備註
 當您安裝 VSIX 套件時，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 會自動執行此命令。 您應該在修補檔案之後執行 `devenv.exe /updateconfiguration`，讓 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 更新 MEF 快取。 這可讓您評估您的修正是否足夠。

## <a name="example"></a>範例
 下列命令列會使 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 套件，並檢查 MEF 快取中的任何變更。

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>另請參閱
 在 Visual Studio [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)[中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
