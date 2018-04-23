---
title: 部署專案類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-project-types"></a>部署專案類型
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 安裝新的專案類型彙總 (ProjectAggregator2.dll) 以及 Windows Installer 封裝 (ProjectAggregator2.msi) 可轉散發。 您必須使用新的彙總工具適用於 managed 程式碼專案類型。 ProjectAggregator2 運作的方法限制[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案造成無法正常運作的 managed 程式碼專案類型的彙總工具。 下列步驟說明如何變更您要使用新的彙總工具的 VSPackage。  
  
1.  從方案中移除 NativeHierarchyWrapper 專案。  
  
2.  移除任何 NativeHierarchyWrapper 二進位檔從您的設定。  
  
3.  將 ProjectAggregator2.msi 加入至您的設定。