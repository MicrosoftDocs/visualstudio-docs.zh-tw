---
title: Visual Studio 中的安全性 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5952b42426f09a0f6e3bcdb6faf318774165f587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484959"
---
# <a name="security-in-visual-studio"></a>Visual Studio 中的安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio 中的安全性](https://docs.microsoft.com/visualstudio/ide/security-in-visual-studio)。  
  
開發應用程式時，從設計到部署的所有層面都應該考慮到安全性。 從一開始就應盡可能安全地執行 Visual Studio。 請參閱[使用者權限](../ide/user-permissions-and-visual-studio.md)。  
  
 為了協助您有效開發安全的應用程式，您應該對安全性概念和開發平台的安全性功能有基本了解， 而且也應該了解安全性編碼技術。  
  
## <a name="understanding-security"></a>了解安全性  
 [安全性](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 描述 .NET Framework 程式碼存取安全性、以角色為基礎的安全性、安全性原則，和安全性工具。  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (程式開發人員不可不知的十大保護程式碼祕訣)  
 說明一些您應該要注意的問題，以免危害資料或系統的安全。  
  
## <a name="coding-for-security"></a>安全性的編碼  
 大部分產生安全性弱點的編碼錯誤，其發生原因是開發人員在處理使用者輸入時做出不正確的假設，或是他們不完全了解其開發中的平台。  
  
 [安全程式碼撰寫方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 提供區分元件以便處理安全性問題的方針。  
  
 [安全性最佳做法](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42)  
 討論緩衝區滿溢 (Buffer Overrun) 和由 /GS 編譯時間旗標所提供之 Microsoft Visual C++ 安全性檢查功能的完整內容。



