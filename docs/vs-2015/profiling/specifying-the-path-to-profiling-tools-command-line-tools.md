---
title: 指定分析工具命令列工具的路徑 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 886c035ddcc14b43200b13d789e59430cf090fdf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731278"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>指定程式碼剖析工具命令列工具的路徑
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼分析工具命令列工具的路徑不會加入 PATH 環境變數中。 在 32 位元電腦上，這些工具會在一個目錄中。 在 64 位元電腦上，程式碼分析工具有 32 位元和 64 位元兩種版本。  
  
## <a name="32-bit-computers"></a>32 位元電腦  
 在 32 位元電腦上，預設的分析工具目錄是*磁碟機*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools。  
  
## <a name="64-bit-computers"></a>64 位元電腦  
 在 64 位元電腦上，則會根據已進行程式碼剖析之應用程式的目標平台指定路徑。  
  
-   若是 32 位元應用程式，預設程式碼剖析工具目錄是：  
  
     *磁碟機*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   若是 64 位元應用程式，預設程式碼剖析工具目錄是：  
  
     *磁碟機*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64



