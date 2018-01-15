---
title: "devenv.exe InstallVSTemplates 參數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

/InstallVSTemplates 參數註冊位於 \<Visual Studio 安裝路徑>\Common7\IDE\ProjectTemplates\ 或 \<Visual Studio 安裝路徑>\Common7\IDE\ItemTemplates\ 中的專案或項目範本，以透過 [新增專案] 和 [新增項目] 對話方塊存取它們。

> [!WARNING]
> 僅 Visual Studio 合作夥伴開發支援此參數。 您必須以系統管理員身分執行 devenv，才能使用 [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) 和 [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) 參數。 如需詳細資訊，請參閱[使用者權限](../../ide/user-permissions-and-visual-studio.md)。

## <a name="syntax"></a>語法

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>另請參閱

[Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)