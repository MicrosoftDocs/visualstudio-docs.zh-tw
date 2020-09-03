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
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196872"
---
# <a name="deploying-project-types"></a>部署專案類型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 會安裝新的專案類型匯總工具 ( # A0) 以及用於轉散發 ( # A1) 的 Windows Installer 套件。 您必須針對 managed 程式碼專案類型使用新的匯總工具。 ProjectAggregator2 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 可避免 managed 程式碼專案類型正常運作的專案匯總工具中的解決方法限制。 下列步驟說明如何將 VSPackage 變更為使用新的匯總工具。  
  
1. 從您的方案中移除 NativeHierarchyWrapper 專案。  
  
2. 從您的安裝程式中移除任何 NativeHierarchyWrapper 的二進位檔。  
  
3. 將 ProjectAggregator2.msi 新增至您的安裝程式。
