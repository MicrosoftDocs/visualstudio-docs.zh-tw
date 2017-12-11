---
title: "一般專案屬性 (Android C++ Makefile) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.openlocfilehash: d7105b75328175abcaba98d062ebeb591ce72d46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="general-project-properties-android-c-makefile"></a>一般專案屬性 (Android C++ Makefile)

屬性 | 說明 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑；可包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑；可包含環境變數。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
組態類型 | 指定此組態產生的輸出類型。 | **動態程式庫 (.so)** - 動態程式庫 (.so)<br>**靜態程式庫 (.a)** - 靜態程式庫 (.a)<br>**公用程式** - 公用程式<br>**Makefile** - Makefile<br>
