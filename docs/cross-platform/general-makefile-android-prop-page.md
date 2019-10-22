---
title: 一般專案屬性 (Android C++ Makefile) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b7fa1b91951e7a3fb145cc26275016037d1b5f2b
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950571"
---
# <a name="general-project-properties-android-c-makefile"></a>一般專案屬性 (Android C++ Makefile)

屬性 | 描述 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑；可包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑；可包含環境變數。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
組態類型 | 指定此組態所產生的輸出類型。 | **動態程式庫 (.so)** - 動態程式庫 ( *.so*)<br>**靜態程式庫 (.a)** - 靜態程式庫 ( *.a*)<br>**公用程式** - 公用程式<br>**Makefile** - Makefile<br>
