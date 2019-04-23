---
title: 部署專案類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e89f74d940182cd92fd15f726676f0979d21186
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047211"
---
# <a name="deploy-project-types"></a>部署專案類型
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 安裝新的專案類型彙總工具 (*ProjectAggregator2.dll*) 和也進行轉散發的 Windows Installer 套件 (*ProjectAggregator2.msi*)。 您必須使用新的彙總工具適用於 managed 程式碼專案類型。 ProjectAggregator2 可解決限制[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案正常運作時，防止 managed 程式碼專案類型的彙總工具。 下列步驟說明如何變更您 VSPackage 也可以使用新的彙總工具。

1. 從您的方案移除 NativeHierarchyWrapper 專案。

2. 移除任何 NativeHierarchyWrapper 二進位檔從您的設定。

3. 新增*ProjectAggregator2.msi*至您的安裝。