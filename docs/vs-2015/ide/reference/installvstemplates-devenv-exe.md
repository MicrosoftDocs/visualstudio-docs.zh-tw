---
title: -InstallVSTemplates (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
ms.assetid: 1fb466f6-7955-4535-a840-d93eb8aaa492
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f019af21beba231a5f135c49fb00dcb463e110
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671006"
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

註冊位於 \Common7\IDE\ProjectTemplates\ 或 \Common7\IDE\ItemTemplates\ 中的專案或專案範本， *\<Visual Studio installation path>* *\<Visual Studio installation path>* 以便透過 [ **新增專案** ] 和 [ **加入新** 專案] 對話方塊來存取這些範本。

> [!WARNING]
> 此參數僅支援進行 Visual Studio 合作夥伴開發，不適用於 Express 版本。 您必須以系統管理員身分執行 devenv，才能使用 [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) 和 [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) 參數。 如需詳細資訊，請參閱[使用者權限](../../ide/user-permissions-and-visual-studio.md)。

## <a name="syntax"></a>語法

```
devenv.exe /InstallVSTemplates
```

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
