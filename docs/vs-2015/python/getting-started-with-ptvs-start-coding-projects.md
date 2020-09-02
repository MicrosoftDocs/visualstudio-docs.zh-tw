---
title: 開始使用 PTVS：開始撰寫程式碼 (專案) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 28622f290d82f86bf3d18cc4f40cfcfc8e953dad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537139"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>開始使用 PTVS：開始撰寫程式碼 (專案)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) 可協助您管理程式碼。 
 
 您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2) 中觀看這些指示。 
 
 如果您曾經使用 Python，您知道您的專案是由檔案在磁碟上的配置所定義。 這適用於純 Python 專案，不過當您有更多檔案時 (使用 JavaScript、單元測試和建置指令碼的網頁)，檔案系統可能開始有點限制。 Visual Studio 使用專案來達成三件事。 
 
- 識別重要的檔案。 重要的檔案是指您簽入版本控制系統的檔案 (原始程式檔、資源等)，而非產生為建置輸出的檔案。 重要的檔案也是指您會複製到另一部電腦，讓其他人可以處理您的應用程式的檔案。 
 
- 指定應該如何使用檔案。 您的檔案可能是每當檔案變更時，工具便需要加以處理的檔案。 Visual Studio 專案可以擷取這項資訊 
 
- 定義您的元件界限。 如果您在應用程式中有多個元件，可以將每個元件放在個別的專案中。 這些可能最後會部署到不同的伺服器、以不同的建置或偵錯設定建置，或甚至是使用 Visual Studio 支援的另一種語言所撰寫，例如 c + + 或 Node.js 
 
  有數個專案範本，以協助您快速入門。 如果您已經有想要處理的 Python 程式碼，[從現有程式碼精靈] 將協助您建立專案，其中包含您的所有檔案。 一些受歡迎的架構有多個 Web 專案存在。 更多範本可在 PTVS 範例組中取得。 有選項可讓提供的 Web 範本搭配其他架構使用。 Python 應用程式範本是全新的空白專案。 有一個模組能讓您開始著手。 
 
  Visual Studio 會在 [方案總管] 視窗中顯示開啟的專案，包括所有檔案、搜尋路徑和 Python 環境。 若要加入新項目，請選取您的專案資料夾並從內容功能表 (按右邊的指標按鈕) 中，依序選擇 [加入]、[新增項目]。 您可以在對話方塊中選取任何項目、自訂項目的名稱，然後將項目加入專案。 
 
  您可以拖放到 [方案總管]。 如果您已經複製檔案到您的專案目錄結構，則可以選擇 [方案總管] 頂端的 [顯示所有檔案]。 然後您可以選取想要加入的項目，並從操作功能表中，選擇 [加入至專案]。 
 
  您可以在這段簡短的 [YouTube 影片 (英文)](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2) 中觀看這些指示。 
 
## <a name="see-also"></a>另請參閱 
 [Wiki 文件 (英文)](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS 快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
