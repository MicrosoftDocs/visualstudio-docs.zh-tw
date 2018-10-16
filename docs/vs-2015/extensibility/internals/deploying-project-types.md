---
title: 部署專案類型 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b54250a32c8c3a24232d2b6a654aeb87fa9a727b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188238"
---
# <a name="deploying-project-types"></a>部署專案類型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 會安裝新的專案類型彙總 (ProjectAggregator2.dll) 以及轉散發 (ProjectAggregator2.msi) 的 Windows Installer 套件。 您必須使用新的彙總工具適用於 managed 程式碼專案類型。 ProjectAggregator2 運作的方法限制[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]專案正常運作時，防止 managed 程式碼專案類型的彙總工具。 下列步驟說明如何變更您 VSPackage 也可以使用新的彙總工具。  
  
1.  從您的方案移除 NativeHierarchyWrapper 專案。  
  
2.  移除任何 NativeHierarchyWrapper 二進位檔從您的設定。  
  
3.  ProjectAggregator2.msi 加入您的設定。

