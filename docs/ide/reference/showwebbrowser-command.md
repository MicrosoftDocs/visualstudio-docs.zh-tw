---
title: "ShowWebBrowser 命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 122a5029c5518d7a4778c4d4732f7ebac9b23683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser 命令
顯示您在 Web 瀏覽器視窗內指定的 URL (不論是在整合式開發環境 (IDE) 內或 IDE 外部)。  
  
## <a name="syntax"></a>語法  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>引數  
 `URL`  
 必要。 網站 URL (統一資源定位器)。  
  
## <a name="switches"></a>參數  
 /new  
 選擇項。 指定頁面會出現在網頁瀏覽器的新執行個體。  
  
 /ext  
 選擇項。 指定頁面會出現在 IDE 外面的預設網頁瀏覽器。  
  
## <a name="remarks"></a>備註  
 **ShowWebBrowser** 命令的別名是 **navigate** 或 **nav**。  
  
## <a name="example"></a>範例  
 下列範例會在 IDE 外面的網頁瀏覽器顯示 MSDN Online 首頁。 如果已經開啟網頁瀏覽器執行個體，便會使用它，否則系統會啟動新的執行個體。  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)