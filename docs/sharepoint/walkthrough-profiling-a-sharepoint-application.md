---
title: 逐步解說：分析 SharePoint 應用程式 |Microsoft Docs
description: 在這個逐步解說中，請使用 Visual Studio 中的程式碼剖析工具，將 SharePoint 應用程式的效能優化。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 796c41ae50a33f00f72e0286d5e9680f9016cf58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952560"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>逐步解說：分析 SharePoint 應用程式
  本逐步解說將示範如何使用 Visual Studio 中的程式碼剖析工具最佳化 SharePoint 應用程式的效能。 範例應用程式是 SharePoint 功能事件接收器，內含的閒置迴圈會降低功能事件接收器的效能。 Visual Studio 分析工具可讓您找出並消除最耗費資源的 (最慢的專案) 部分，也稱為最忙碌 *路徑*。

 本逐步解說將示範下列工作：

- [新增功能和功能事件接收器](#add-a-feature-and-feature-event-receiver)。

- [設定和部署 SharePoint 應用程式](#configure-and-deploy-the-sharepoint-application)。

- [執行 SharePoint 應用程式](#run-the-sharepoint-application)。

- [查看並解讀設定檔結果](#view-and-interpret-the-profile-results)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 Microsoft Windows 和 SharePoint 版本。

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>建立 SharePoint 專案
 首先，建立 SharePoint 專案。

### <a name="to-create-a-sharepoint-project"></a>若要建立 SharePoint 專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [範本] 窗格中，選擇 [ **SharePoint 2010] 專案** 範本。

4. 在 [ **名稱** ] 方塊中，輸入 **ProfileTest**，然後選擇 [ **確定]** 按鈕。

    [ **SharePoint 自訂] Wizard** 隨即出現。

5. 在 [ **指定偵錯工具的網站和安全性等級** ] 頁面上，輸入您要在其中偵測網站定義的 SharePoint 伺服器網站的 URL，或使用預設位置 (HTTP://<em>系統名稱</em>/) 。

6. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕。

    目前您只能分析陣列方案。 如需有關沙箱化方案與伺服器陣列方案的詳細資訊，請參閱 [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 選擇 [完成] 按鈕。 專案隨即出現在 **方案總管** 中。

## <a name="add-a-feature-and-feature-event-receiver"></a>新增功能和功能事件接收器
 接下來，在專案中加入功能與功能的事件接收器。 這個事件接收器會包含要分析的程式碼。

### <a name="to-add-a-feature-and-feature-event-receiver"></a>若要加入功能和功能事件接收器

1. 在 **方案總管** 中，開啟 [ **功能** ] 節點的快捷方式功能表，選擇 [ **加入功能**]，並將名稱保留為預設值 [ **Feature1**]。

2. 在 **方案總管** 中，開啟 **Feature1** 的快捷方式功能表，然後選擇 [ **加入事件接收器**]。

     這樣會將程式碼檔案加入至具有多個標記為註解之事件處理常式的功能，並開啟檔案進行編輯。

3. 在事件接收器類別中，加入下列變數宣告。

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. 使用下列程式碼取代 `FeatureActivated` 程序。

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try
    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. 在程式下方新增下列程式 `FeatureActivated` 。

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. 在 **方案總管** 中，開啟專案的快捷方式功能表 ([ **ProfileTest** ]) ，然後選擇 [ **屬性**]。

7. 在 [ **屬性** ] 對話方塊中，選擇 [ **SharePoint** ] 索引標籤。

8. 在 [使用中的 **部署** 設定] 清單中，選擇 [ **未啟用**]。

     選取這個部署組態可讓您之後在 SharePoint 中手動啟用這個功能。

9. 儲存專案。

## <a name="configure-and-deploy-the-sharepoint-application"></a>設定和部署 SharePoint 應用程式
 現在 SharePoint 專案已就緒，請設定它並將它部署至 SharePoint 伺服器。

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>若要設定和部署 SharePoint 應用程式

1. 在 [ **分析** ] 功能表上，選擇 [ **啟動效能分析]**。

2. 在 [ **效能] 嚮導** 的第一個頁面上，將分析的方法保留為 **CPU 取樣** ，然後選擇 [ **下一步]** 按鈕。

     其他程式碼剖析方法可在進階的程式碼剖析情況下使用。 如需詳細資訊，請參閱[了解效能收集方法](../profiling/understanding-performance-collection-methods.md)。

3. 在 [ **效能] 嚮導** 的第二頁上，將設定檔目標保留為 **ProfileTest** ，然後選擇 [ **下一步]** 按鈕。

     如果方案中有多個專案，這些專案都會出現在這個清單中。

4. 在 [ **效能] 嚮導** 的第三頁上，清除 [ **啟用階層互動分析]** 核取方塊，然後選擇 [ **下一步]** 按鈕。

     [階層互動分析] (TIP) 功能對於測量查詢資料庫之應用程式的效能，以及顯示網頁的要求次數來說很有用。 不過，這個範例中不需要這項資料，因此我們將不會啟用這個功能。

5. 在 [ **效能] 嚮導** 的第四頁上，將 [ **Wizard 完成後啟動分析]** 核取方塊保留為已選取狀態，然後選擇 [ **完成** ] 按鈕。

     Wizard 會在伺服器上啟用應用程式分析、顯示 **效能總管** 視窗，然後建立、部署和執行 SharePoint 應用程式。

## <a name="run-the-sharepoint-application"></a>執行 SharePoint 應用程式
 啟用 SharePoint 中的功能，觸發 `FeatureActivation` 事件程式碼使其執行。

### <a name="to-run-the-sharepoint-application"></a>若要執行 SharePoint 應用程式

1. 在 SharePoint 中，開啟 [ **網站動作** ] 功能表，然後選擇 [ **網站設定**]。

2. 在 [ **網站動作** ] 清單中，選擇 [ **管理網站功能** ] 連結。

3. 在 [**功能**] 清單中，選擇 [ **ProfileTest Feature1**] 旁的 [**啟用**] 按鈕。

     由於會在 `FeatureActivated` 函式中呼叫閒置迴圈，因此當您執行這項操作時會暫停。

4. 在 **快速啟動** 列上，選擇 [ **清單** ]，然後在 [ **清單** ] 清單中選擇 [ **宣告**]。

     您會發現清單中已加入一項新公告，說明功能已啟動。

5. 關閉 SharePoint 網站。

     關閉 SharePoint 之後，分析工具會建立並顯示範例分析報表，並將它儲存為 **ProfileTest** 專案資料夾中的 .vsp 檔案。

## <a name="view-and-interpret-the-profile-results"></a>查看和解讀設定檔結果
 現在您已執行並分析 SharePoint 應用程式，接下來要檢視測試結果。

### <a name="to-view-and-interpret-the-profile-results"></a>若要查看及解讀設定檔結果

1. 在範例分析報告的 [ **執行最多個別工作** 的函式] 區段中，請注意 `TimeCounter` 位於清單頂端附近。

     這個位置指出 `TimeCounter` 是其中一個擁有最多樣本數目的函式，表示它是應用程式中最大的效能瓶頸之一。 不過，這種情形並不意外，因為它是為了方便示範而刻意設計成這樣。

2. 在 [ **執行最多個別工作** 的函式] 區段中，選擇 [] `ProcessRequest` 連結以顯示函數的成本分佈 `ProcessRequest` 。

     在的 [ **呼叫** 的函式] 區段中 `ProcessRequest` ，請注意， **FeatureActiviated** 函式會列為最耗費資源的被呼叫函數。

3. 在 [ **呼叫** 的函式] 區段中，選擇 [ **FeatureActivated** ] 按鈕。

     在 **FeatureActivated** 的 [**被呼叫** 的函式] 區段中，此函式 `TimeCounter` 會列為最耗費資源的已呼叫函數。 在 [函式程式 **代碼視圖** ] 窗格中，反白顯示的程式碼 (`TimeCounter`) 是作用點，並指出需要更正的位置。

4. 關閉樣本分析報告。

     若要隨時重新查看報表，請在 **效能總管** 視窗中開啟 .vsp 檔案。

## <a name="fix-the-code-and-reprofile-the-application"></a>修正程式碼並 reprofile 應用程式
 現在已找出 SharePoint 應用程式中的作用點函式，加下來要進行修正。

### <a name="to-fix-the-code-and-reprofile-the-application"></a>若要修正程式碼並重新分析應用程式

1. 在功能事件接收器程式碼中，將 `TimeCounter` 中的 `FeatureActivated` 方法呼叫標記為註解，以防止呼叫它。

2. 儲存專案。

3. 在 **效能總管** 中，開啟 [目標] 資料夾，然後選擇 [ **ProfileTest** ] 節點。

4. 在 [ **效能總管** ] 工具列的 [ **動作** ] 索引標籤中，選擇 [ **開始分析** ] 按鈕。

     如果您想要在重新分析應用程式之前變更任何分析屬性，請改為選擇 [ **啟動效能] Wizard** 按鈕。

5. 遵循本主題先前的執行 **SharePoint 應用程式** 一節中的指示。

     現在功能啟動的速度應該加快許多，因為已消除呼叫閒置迴圈。 樣本分析報告應該會反映這種情況。

## <a name="see-also"></a>另請參閱
- [效能會話總覽](../profiling/performance-session-overview.md)
- [效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)
- [Find Application Bottlenecks with Visual Studio Profiler](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler) (使用 Visual Studio 分析工具尋找應用程式瓶頸)