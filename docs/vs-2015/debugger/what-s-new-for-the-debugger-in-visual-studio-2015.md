---
title: 什麼是 Visual Studio 2015 中偵錯工具的新功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859233c1c79360f28e306dc0fca7df574cb39ccf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774883"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Visual Studio 2015 中偵錯工具的新功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2015 Update 1 偵錯和診斷之全部新功能的詳細資訊，請參閱 [Visual Studio 2015 Update 1 版本資訊](https://www.visualstudio.com/news/vs2015-update1-vs#debug)。  
  
 如需 Visual Studio 2015 RTM 偵錯和診斷之全部新功能的詳細資訊，請參閱 [Visual Studio 2015 版本資訊](https://www.visualstudio.com/news/vs2015-vs#debug)。  
  
## <a name="visual-studio-2015-update-1-changes"></a>Visual Studio 2015 Update 1 的變更  
 C++ [編輯及繼續] 支援更多功能。 如需詳細資訊，請參閱 <<c0> [ 編輯後繼續 （Visual c + +）](../debugger/edit-and-continue-visual-cpp.md)。  
  
 為偵錯 Visual C++ 存取違規，新的例外狀況對話方塊會指定造成例外狀況的指標。 如需詳細資訊，請參閱 [How Can I Debug an Access Violation?](../debugger/how-can-i-debug-an-access-violation-q.md) 和 [Visual Studio 2015 Update 1 中的偵錯 C++ 存取違規改良](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Visual Studio 2015 RTM 偵錯工具 UI 和熱鍵的變更  
 在 [例外狀況] 和 [中斷點]  UI 中有幾項重大 UI 變更。  
  
### <a name="breakpoints"></a>中斷點  
 Visual Studio 2015 有新的中斷點設定方式，也就是 [中斷點設定]  視窗。  
  
 以下是 [中斷點] 主視窗和快速鍵的摘要：  
  
|功能|功能表的位置|熱鍵|  
|-------------|-------------------|------------|  
|新增中斷點，切換中斷點|**偵錯] / [切換中斷點**<br /><br /> 在編輯器中的內容功能表 / [插入中斷點] <br /><br /> 在左邊界中按一下|F9|  
|新增函式中斷點|**偵錯 / 新增中斷點 / 函式中斷點**|在 Visual Studio 2015 RTM （含更新），使用 ALT + F9 和 alt + B<br /><br /> 在 Visual Studio 2015 Update 1 和更新版本中，使用 CTRL + B|  
|[中斷點] 視窗|**偵錯 / Windows / 中斷點**|CTRL + ALT + B|  
|、[條件] |在中斷點上的內容功能表 / [條件] |ALT + F9、C|  
|、[條件] |在中斷點上的內容功能表 / [動作] |沒有熱鍵|  
  
 如需詳細資訊，請參閱下列文章：  
  
1.  [使用中斷點](../debugger/using-breakpoints.md)  
  
2.  [新中斷點組態體驗](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [中斷點組態體驗](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>例外狀況設定  
 新的 [例外狀況設定]  視窗可讓您指定要用於單一例外狀況或某一分類之例外狀況的例外狀況處理種類。  
  
|功能|功能表的位置|熱鍵|  
|-------------|-------------------|------------|  
|[例外狀況設定] 視窗|**偵錯 / Windows / 例外狀況設定**|CTRL + ALT + E|  
  
 如需詳細資訊，請參閱下列文章：  
  
1.  [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [新的例外狀況視窗](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>編輯後繼續  
 在 Visual Studio 2015，您可以在 [工具] / [選項] / [偵錯] / [一般]  頁面設定 [編輯後繼續]。 在舊版中，這些設定是在不同的選項類別。  
  
### <a name="attach-to-process"></a>附加至處理序  
 在 Visual Studio 2015，[附加至處理序] 命令只能在 [偵錯] 功能表中使用。 在舊版中已經可以從 [工具] 功能表中使用。 CTRL + ALT + P 熱鍵適用於所有版本。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)



