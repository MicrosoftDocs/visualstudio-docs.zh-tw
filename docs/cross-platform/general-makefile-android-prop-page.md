---
title: 一般專案屬性 (Android C++ Makefile) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5ac5c50a1bf7c6f0d9046f136ad821370b59ad0a
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252306"
---
# <a name="general-project-properties-android-c-makefile"></a>一般專案屬性 (Android C++ Makefile)

屬性 | 描述 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑；可包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑；可包含環境變數。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
組態類型 | 指定此組態所產生的輸出類型。 | **動態程式庫 (.so)** - 動態程式庫 (*.so*)<br>**靜態程式庫 (.a)** - 靜態程式庫 (*.a*)<br>**公用程式** - 公用程式<br>**Makefile** - Makefile<br>
