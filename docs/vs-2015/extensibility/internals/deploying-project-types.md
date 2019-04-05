---
title: 部署專案類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f168656950c65ce133a8e808a0fa1232726e1b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939710"
---
# <a name="deploying-project-types"></a>部署專案類型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 會安裝新的專案類型彙總 (ProjectAggregator2.dll) 以及轉散發 (ProjectAggregator2.msi) 的 Windows Installer 套件。 您必須使用新的彙總工具適用於 managed 程式碼專案類型。 ProjectAggregator2 運作的方法限制[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]專案正常運作時，防止 managed 程式碼專案類型的彙總工具。 下列步驟說明如何變更您 VSPackage 也可以使用新的彙總工具。  
  
1.  從您的方案移除 NativeHierarchyWrapper 專案。  
  
2.  移除任何 NativeHierarchyWrapper 二進位檔從您的設定。  
  
3.  ProjectAggregator2.msi 加入您的設定。
