---
title: 開始使用 PTVS：在 Azure 建置網站 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 61f8748a3874f32db9c235d03b6b7464bc5cecf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62550996"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>開始使用 PTVS：在 Azure 建置網站
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以快速地開始在 Azure 中建置 Python 網站。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) 中觀看這些指示。  
  
 從 [新增專案] 對話方塊開始，並在 Python 專案底下選擇 [Bottle Web 專案]。  此 [Bottle](http://bottlepy.org/docs/dev/index.html) 範本是以[啟動程序架構 (英文)](http://getbootstrap.com/) 為基礎的入門網站。  當您建立專案時，Visual Studio 會提示您在虛擬環境安裝相依性 (在此情況下為 Bottle)。  因為您要部署至 Azure 網站，您需要將相依性加入虛擬環境，以便部署您的網站作業的必要部分。  您的環境也需要根據 Python 2.7 或 3.4 32 位元。  一旦建立專案之後，請按 F5 開始在本機執行您的網站。  
  
 在 Azure 中嘗試網站很容易。  如果您沒有 Azure 訂用帳戶，您可以使用 [try.azurewebsites.net](https://trywebsites.azurewebsites.net/)。  這個網站提供簡單的方式來試用 Azure 網站一個小時，且只使用社交登入。  您不需要使用信用卡。  在 [變更語言] 下拉式清單中選擇 [空白網站] 範本，然後選擇 [建立]。  在 [使用您的 Web 應用程式] 下，選擇 [下載發行設定檔]，並儲存檔案以便用於 Visual Studio。  您也可以使用 git 從任何作業系統部署。  
  
 切換回 Visual Studio 和您建立的專案。  在 [方案總管] 中選取您的專案節點、選擇正確的指標按鈕，然後選擇 [發行]。  如果您有 Azure 訂用帳戶，您可以在對話方塊中按一下 Microsoft Azure 網站，從這裡管理您的網站。  在此逐步解說中，選擇 [匯入] 可匯入您剛才下載的發行設定檔。  因為發行設定檔已具備所有必要的資訊，您可以選擇 [發行]。  在幾秒鐘的時間便會開啟新的瀏覽器視窗，您的網站已即時裝載於 Azure 雲端。  
  
 簡易網站很簡單，不過如需 Azure 中更重要的 Web 應用程式的相關資訊，請參閱[深入探討](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10)影片，以及此頻道中的其他影片 (在入門或深入探討影片頁面右上方的連結，以及下面的連結。  
  
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) 中觀看這些指示。  
  
## <a name="see-also"></a>請參閱  
 [Wiki 文件 (英文)](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [PTVS 快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
