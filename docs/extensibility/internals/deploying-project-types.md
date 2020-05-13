---
title: 部署項目型態 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708781"
---
# <a name="deploy-project-types"></a>部署項目類型
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]安裝一個新的項目類型聚合器 *(Project聚合器2.dll*)以及用於重新分發的 Windows 安裝程式套件 (*ProjectAg 聚合器 2.msi*)。 您必須將新的聚合器用於託管代碼項目類型。 ProjectAg聚合器2圍繞[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案聚合器中阻止託管代碼項目類型正常工作的限制進行工作。 以下步驟描述如何更改 VSPackage 以使用新的聚合器。

1. 從解決方案中刪除本機層次結構包裝器專案。

2. 從設置中刪除任何本機層次結構包裝二進位檔。

3. 將*Project 聚合器2.msi*添加到您的設定中。
