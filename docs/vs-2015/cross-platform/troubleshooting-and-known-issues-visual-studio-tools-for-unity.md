---
title: 疑難排解和已知問題 (Visual Studio Tools for Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297666"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>疑難排解和已知問題 (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本節中，您將找到 Visual Studio Tools for Unity 之常見問題的解決方法、已知問題的描述，並了解如何透過回報錯誤來協助改善 Visual Studio Tools for Unity。  
  
## <a name="troubleshooting"></a>疑難排解  
 若要解決 Visual Studio Tools for Unity 的一些常見問題，請參閱下列各節。  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>從 UnityVS 移轉至 Visual Studio Tools for Unity  
 如果您要從 UnityVS 移轉至 Visual Studio Tools for Unity，您必須為 Unity 專案產生新的 Visual Studio 方案。  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>將 Unity 專案從 UnityVS 1.8 移轉至 Visual Studio Tools for Unity 1.9  
  
1. 從您的 Unity 專案中刪除舊的方案和專案檔。 在您的 Unity 專案根目錄中，找出並刪除所有 Visual Studio .sln 和 .*proj 檔。  
  
2. 將 Visual Studio Tools for Unity 套件匯入 Unity 專案。 如需如何匯入 VSTU 套件的相關資訊，請參閱 [使用者入門](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) 頁面上的＜設定 Visual Studio Tools for Unity＞。  
  
3. 產生新的方案和專案檔。 如果您想要立即產生檔案，請在 Unity Editor 主功能表上，選擇 [Visual Studio Tools] ****、[Generate Project Files] ****。 否則，您可以視需要略過這個步驟；當您選擇 [Visual Studio Tools] ****、[Open in Visual Studio] **** 時，Visual Studio Tools for Unity 會自動產生新檔案。  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio 不會載入 Visual Studio Tools for Unity 所建立的方案  
 如需詳細資訊，請參閱 [這個 stackoverflow 問題的答案](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907)。  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>在 Windows 8 上，Visual Studio 會要求下載 Unity 目標 Framework  
 UnityVS 需要 .NET Framework 3.5，但 Windows 8 上預設並未安裝。 若要修正這個問題，請遵循指示下載並安裝 .Net Framework 3.5。  
  
## <a name="known-issues"></a>已知問題  
 Visual Studio Tools for Unity 在偵錯工具如何與 Unity 的舊版 C# 編譯器互動方面有已知問題。 我們致力於協助修正這些問題，但您同時可能會遇到下列問題。  
  
- 偵錯時，Unity 有時會損毀。  
  
- 偵錯時，Unity 有時會凍結。  
  
- 逐步執行和跳離方法有時運作異常，尤其是在 iterator 或 switch 陳述式內。  
  
## <a name="reporting-errors"></a>報告錯誤  
 當您遇到損毀、凍結或其他錯誤時，請傳送錯誤報告，以協助我們改善 Visual Studio Tools for Unity 的品質。 這可協助我們調查並修正 Visual Studio Tools for Unity 的問題。 感謝您！  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>如何在 Visual Studio 凍結時回報錯誤  
 根據報告，當使用 Visual Studio Tools for Unity 進行偵錯時，Visual Studio 有時會凍結，不過我們需要更多資料來了解這個問題。 您可以執行下列步驟來協助我們進行調查。  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>回報使用 Visual Studio Tools for Unity 進行偵錯時 Visual Studio 凍結的情形  
  
1. 開啟新的 Visual Studio 執行個體。  
  
2. 開啟 [附加至處理序] 對話方塊。 在新的 Visual Studio 執行個體的主功能表上，選擇 [偵錯] ****、[附加至處理序] ****。  
  
3. 將偵錯工具附加至 Visual Studio 的已凍結執行個體。 在 [附加至處理序] **** 對話方塊中，從 [可使用的處理序] **** 資料表選取 Visual Studio 的已凍結執行個體，然後選擇 [附加] **** 按鈕。  
  
4. 暫停偵錯工具。 在 Visual Studio 的新實例的主功能表上，選擇 [ **Debug**]、[ **全部中斷** ]，或直接按 **Ctrl + Alt + Break**。  
  
5. 建立執行緒傾印。 在 [命令視窗] 中，輸入下列命令，然後按 **enter**鍵。  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    您可能需要先顯示 [命令] **** 視窗。 在 Visual Studio 主功能表上，選擇 [檢視] ****、[其他視窗] ****、[命令視窗] ****。  
  
6. 最後，將執行緒傾印傳送至 [vstusp@microsoft.com](mailto:vstusp@microsoft.com) ，以及當 Visual Studio 變成凍結時所執行之工作的描述。
