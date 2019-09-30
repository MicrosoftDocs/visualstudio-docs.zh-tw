---
title: 開始使用 Unity 來建置遊戲
description: 開始使用 Unity 和 Visual Studio for Mac
author: asb3993
ms.author: amburns
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: ff8fe1b2b4efe7ff91d3b363c58183be534a1441
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108420"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中使用 Unity 開始建置遊戲

Unity 是一款遊戲引擎，可讓您使用 C# 開發遊戲。 本逐步解說示範如何使用 Visual Studio for Mac 和 Visual Studio for Mac Tools for Unity 延伸模組以及 Unity 環境，開始開發和偵錯 Unity 遊戲。

Visual Studio for Mac Tools for Unity 是免費的延伸模組，隨 Visual Studio for Mac 一起安裝。 它可讓 Unity 開發人員利用 Visual Studio for Mac 的產能功能，包括極佳的 IntelliSense 支援、偵錯功能等。

## <a name="objectives"></a>目標

> [!div class="checklist"]
> * 深入了解使用 Visual Studio for Mac 進行 Unity 開發

## <a name="prerequisites"></a>必要條件

- Visual Studio for Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition (個人版) 或更高版本 ([https://store.unity.com](https://store.unity.com/)，需要 unity.com 帳戶才能執行)

## <a name="intended-audience"></a>適用對象

本實驗適用於熟悉 C# 的開發人員，但不需要深度經驗。

## <a name="task-1-creating-a-basic-unity-project"></a>工作 1：建立基本的 Unity 專案

1. 啟動 **Unity**。 如果系統要求，請登入。

2. 按一下 [新增]  。

    ![Unity 中的 [New] \(新增\) 按鈕](media/unity-image1.png)

3. 將專案名稱  設定為 **"UnityLab"** ，然後選取 [3D]  。 按一下 [Create project]  \(建立專案\)。

    ![建立新的專案畫面](media/unity-image2.png)

4. 您現在看到的是 Unity 的預設介面。 它的左側是遊戲物件的場景階層，中間顯示的空白場景是 3D 檢視，底部為專案檔案窗格，以及右側的屬性編輯器和服務。 當然，除此之外還有更多，但這些都是一些更重要的元件。

    ![空白的 Unity 介面](media/unity-image3.png)

5. 針對剛接觸 Unity 的開發人員，應用程式中執行的所有內容都將存在於**場景**的內容中。 場景檔案是單一檔案，其中包含專案中針對目前的場景和其屬性所使用之資源相關的各種中繼資料。 當您針對某個平台封裝您的應用程式時，產生的應用程式最終將成為一或多個場景的集合，再加上您新增的任何與平台相關的程式碼。 您可以在專案中擁有所需數量的場景。

6. 新場景中只有一個相機及一個定向光線。 場景需要**相機**才能看到任何內容，而**音訊接聽程式**則讓任何聲音可以聽見。 這些元件會附加到 **GameObject**。

7. 從 [Hierarchy]  \(階層\) 窗格中選取 [Main Camera]  \(主相機\) 物件。

    ![階層窗格中反白顯示的主相機物件](media/unity-image4.png)

8. 從視窗右側選取 **Inspector** \(屬性編輯器\) 窗格以檢閱其屬性。 相機屬性包含轉換資訊、背景、投射類型、視野等等。 預設情況下還加入了一個音訊接聽程式元件，它實際上是從連接到相機的虛擬麥克風，轉譯場景的音訊。

    ![屬性編輯器窗格](media/unity-image5.png)

9. 選取 [Directional Light]  \(定向光線\) 物件。 這為場景提供了光線，因此著色器等元件知道如何轉譯物件。

    ![反白顯示的定向光線物件](media/unity-image6.png)

10. 使用 **Inspector** 可以看到它包含常見的光源屬性，包括類型、色彩、濃度、陰影類型等等。

    ![在屬性編輯器窗格中查看屬性](media/unity-image7.png)

11. 重要的是要指出 Unity 中的專案與 Visual Studio for Mac 的對應項目稍有不同。 在底部的 [Project]  \(專案\) 索引標籤中，以滑鼠右鍵按一下 [Assets]  \(資產\) 資料夾，然後選取 [Reveal in Finder]  \(在 Finder 中顯示\)。

    ![在 Finder 內容動作中顯示](media/unity-image8.png)

12. 如您所見，Projects 包含 [Assets]  \(資產\)、[Library]  \(程式庫\)、[ProjectSettings]  \(專案設定\) 和 [Temp]  \(暫存\) 資料夾。 不過，唯一在介面中顯示的是 [Assets]  資料夾。 [Library]  資料夾是匯入資產的本機快取，它會保留資產的所有中繼資料。 [ProjectSettings]  資料夾會儲存您可以設定的設定。 在建置程序中，[Temp]  資料夾會用於 Mono 和 Unity 的暫存檔案。 還有一個方案檔，您可以在 Visual Studio for Mac 中開啟 (此處為 **UnityLab.sln**)。

    ![在 Finder 中的 Assets](media/unity-image9.png)

13. 關閉 [Finder]  視窗並返回 **Unity**。

14. [Assets]  資料夾包含您的所有資產 - 美工圖案，程式碼、音訊等等。現在它是空的，但是您放入專案的每一個檔案都在這裡。 這始終是 **Unity 編輯器**中最上層的資料夾。 但一律透過 Unity 介面 (或 Visual Studio for Mac) 新增和移除檔案，而不是直接透過檔案系統。

    ![Unity 中的 [Assets] 資料夾](media/unity-image10.png)

15. **GameObject** 是 Unity 開發的核心，因為幾乎所有項目都來自該類型，包括模型、光線、粒子系統等等。 透過 [GameObject] \(遊戲物件\) > [3D Object] \(3D 物件\) > [Cube]  \(立方體\) 功能表將新的 **Cube** 物件新增至場景中。

    ![場景中的立方體物件](media/unity-image11.png)

16. 快速查看新的 **GameObject** 的屬性，並看到它有一個名稱、標記、圖層和轉換。 所有 **GameObjects** 都有這些屬性。 此外，數個元件已連結至 **Cube** 以提供所需的功能，包括網格篩選條件，方塊碰撞器和轉譯器。

    ![遊戲物件屬性](media/unity-image12.png)

17. 將 **Cube** 物件 (預設名稱為 **"Cube"** ) 重新命名為 **"Enemy"** 。 請務必按下 **Enter** 以儲存變更。 這將是我們簡單遊戲中的敵人立方體。

    ![立方體物件重新命名屬性](media/unity-image13.png)

18. 使用與上面相同的程序將另一個 **Cube** 物件新增到場景中，並將其命名為 **"Player"** 。

    ![重新命名第二個立方體物件](media/unity-image14.png)

19. 也將玩家物件標記為 **"Player"** (請參閱 [名稱] 欄位下的 **Tag** \(標記\) 下拉式清單控制項)。 我們將在敵人指令碼中使用它來協助找出玩家的遊戲物件。

    ![標記玩家物件](media/unity-image15.png)

20. 在 [Scene]  \(場景\) 檢視中，使用滑鼠沿著 Z 軸移動玩家物件遠離敵人物件。 您可以藉由選取**紅色**面板，朝**藍色**線條拖曳立方體來沿 Z 軸移動。 由於立方體存在於 3D 空間中，但每次只能在 2D 中拖曳，因此拖曳的軸特別重要。

    ![顯示立方體的 [場景] 檢視](media/unity-image16.png)

21. 沿著軸向下和向右移動立方體。 這會更新 **Inspector** 中的 **Transform.Position** 屬性。 請務必拖曳至類似此處所顯示的位置，以在實驗室中更輕鬆地完成後續步驟。

    ![沿著軸移動一個立方體](media/unity-image17.png)

22. 現在您可以新增一些程式碼來驅動敵人的邏輯，使它追逐玩家。 以滑鼠右鍵按一下 [Project]  索引頁中的 [Assets]  資料夾，然後選取 [Create] \(建立\) > [C# Script]  \(C# 指令碼\)。

    ![C# 指令碼內容動作](media/unity-image18.png)

23. 將新的 C# 指令碼命名為 **"EnemyAI"** 。

    ![C# 指令碼](media/unity-image19.png)

24. 若要將指令碼附加至遊戲物件，請將新建立的指令碼拖曳至 [Hierarchy]  窗格中的 **Enemy** 物件上。 現在該物件會使用此指令碼的行為。

    ![反白顯示將指令碼新增至遊戲物件](media/unity-image20.png)

25. 選取 [File] \(檔案\) > [Save Scenes]  \(儲存場景\) 以儲存目前場景。 將它命名為 **"MyScene"** 。

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>工作 2：使用 Visual Studio for Mac Tools for Unity

1. 編輯 C# 程式碼的最佳方法是使用 Visual Studio for Mac。 您可以將 Unity 設定為使用 Visual Studio for Mac 作為其預設處理常式。 選取 [Unity] > [Preferences]  \(喜好設定\)。

2. 選取 [External Tools]  \(外部工具\) 索引標籤。從 [External Script Editor]  \(外部指令碼編輯器\) 下拉式清單中，選取 [Browse]  \(瀏覽\)，並選取 [應用程式]/[Visual Studio.app]  。 或者，如果已經有 [Visual Studio]  選項，請直接選取該選項。

    ![喜好設定中的 [外部工具] 索引標籤](media/unity-image21.png)

3. Unity 現在已設定為使用 **Visual Studio for Mac** 進行指令碼編輯。 關閉 [Unity Preferences]  \(Unity 喜好設定\) 對話方塊。

    ![在喜好設定中已選取 Visual Studio](media/unity-image22.png)

4. 按兩下 [EnemyAI.cs]  ，在 **Visual Studio for Mac** 中開啟它。

    ![在 Unity 中已選取敵人資產](media/unity-image23.png)

5. Visual Studio 方案很簡單。 它包含 [Assets]  資料夾 (來自 [Finder]  的相同資料夾) 和稍早建立的 **EnemyAI.cs** 指令碼。 在更複雜的專案中，階層可能與您在 Unity 中看到的不同。

    ![Visual Studio for Mac 中的 [解決方案] 索引頁](media/unity-image24.png)

6. **EnemyAI.cs** 會在編輯器中開啟。 初始的指令碼僅包含 **Start** 和 **Update** 方法的虛設常式。

7. 使用下列程式碼取代初始的敵人程式碼。

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. 快速查看這裡所定義的簡單敵人行為。 在 **Start** 方法中，我們取得了對玩家物件 (透過其標記) 的參考，以及它的**轉換**。 在 **Update** 方法中 (每個畫面格都會呼叫)，敵人將朝向玩家物件移動。 關鍵字和名稱使用色彩編碼，以便更容易了解 Visual Studio for Mac 中的程式碼基底。

9. 將變更儲存至 **Visual Studio for Mac** 中的敵人指令碼。

## <a name="task-3-debugging-the-unity-project"></a>工作 3：偵錯 Unity 專案

1. 在 **Start** 方法的第一行程式碼上設定中斷點。 您可以按一下目標行的編輯器邊界，或將游標放在該行上，然後按 **F9**。

    ![在 Visual Studio for Mac 中設定中斷點](media/unity-image25.png)

2. 按一下 [開始偵錯]  按鈕或按 **F5**。 這會建置專案，並將其附加至 Unity 進行偵錯。

    ![Visual Studio for Mac 中的啟動按鈕](media/unity-image26.png)

3. 返回 **Unity**，然後按一下 [Run]  \(執行\) 按鈕來開始遊戲。

    ![Unity 中的 [Run] \(執行\) 按鈕](media/unity-image27.png)

4. 應該會叫用中斷點，您現在可以使用 Visual Studio for Mac 偵錯工具。

    ![Visual Studio for Mac 中的中斷點叫用](media/unity-image28.png)

5. 從 [區域變數]  索引頁中，找到 [this]  指標，該指標參考 **EnemyAI** 物件。 展開參考，並查看您可以瀏覽相關聯的成員，例如 [Speed]  \(速度\)。

    ![Visual Studio for Mac 中的區域變數偵錯索引頁](media/unity-image29.png)

6. 從 **Start** 方法中移除中斷點，方法與新增它的方式相同 - 透過在邊界中按一下它，或選取行並按 **F9**。

    ![Visual Studio for Mac 中的中斷點叫用](media/unity-image30.png)

7. 按 **F10** 不進入使用標記作為參數尋找 **Player** 遊戲物件的第一行程式碼。

8. 將滑鼠游標暫留在程式碼編輯器視窗中的 **player** 變數上，以檢視其相關聯的成員。 您甚至可以展開重疊以檢視子系屬性。

    ![Visual Studio for Mac 編輯器中的偵錯視窗](media/unity-image31.png)

9. 按 **F5** 或按 [執行]  按鈕以繼續執行。 返回 Unity，以查看敵人立方體反覆接近玩家立方體。 如果看不到相機，您可能需要調整相機。

    ![在 Unity 中播放的場景](media/unity-image32.png)

10. 切換回 **Visual Studio for Mac** 並在 **Update** 方法的第一行設定中斷點。 它應該會立即叫用。

    ![在 Visual Studio for Mac 中設定中斷點](media/unity-image33.png)

11. 假設速度太快，我們想要在不重新啟動應用程式的情況下測試變更的影響。 在 [自動變數]  或 [區域變數]  視窗中找到 **Speed** 變數，然後將它變更為 **"10"** 並按 **Enter**。

    ![調整 [區域變數] 視窗中的變數](media/unity-image34.png)

12. 移除中斷點，並按 **F5** 以繼續執行。

13. 返回 **Unity** 以檢視執行中的應用程式。 敵人立方體現在以原始速度的五分之一移動。

    ![包含執行中應用程式的 Unity 視窗](media/unity-image35.png)

14. 再次按一下 [Play]  \(播放\) 按鈕停止 Unity 應用程式。

    ![停止 Unity 應用程式](media/unity-image36.png)

15. 返回 **Visual Studio for Mac**。 按一下 [停止]  按鈕停止偵錯工作階段。

    ![在 Visual Studio for Mac 中停止偵錯工作階段](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>工作 4：探索 Visual Studio for Mac 中的 Unity 功能

1. Visual Studio for Mac 可在程式碼編輯器中快速存取 Unity 文件。 將游標放在 **Update** 方法內 **Vector3** 符號上的某處，然後按 **⌘ Command + '** 。

    ![在 Visual Studio for Mac 編輯器中選取方法](media/unity-image38.png)

2. 新的瀏覽器視窗隨即開啟，其中包含 **Vector3** 的文件。 您可自行關閉瀏覽器視窗。

    ![開啟至文件的瀏覽器視窗](media/unity-image39.png)

3. Visual Studio for Mac 還提供了一些協助程式來快速建立 Unity 行為類別。 從 [方案總管]  中，以滑鼠右鍵按一下 [資產]  ，然後選取 [新增] > [新增 MonoBehaviour]  。

    ![新增 MonoBehaviour 內容動作](media/unity-image40.png)

4. 新建立的類別會為 **Start** 和 **Update** 方法提供虛設常式。 在 **Update** 方法的右括號之後，開始鍵入 **"onmouseup"** 。 在您輸入時，請注意 Visual Studio 的 IntelliSense 會快速選出您計劃要實作的方法。 從提供的自動完成清單中選取它。 它將為您填寫方法虛設常式，包括任何參數。

    ![Visual Studio for Mac 中的 Intellisense](media/unity-image41.png)

5. 在 **OnMouseUp** 方法內，輸入 **"base."** 以查看所有可呼叫的基底方法。 您還可以使用 IntelliSense 飛出視窗右上角的分頁選項，探索每個函式不同的多載。

    ![探索 Visual Studio for Mac 中的多載](media/unity-image42.png)

6. Visual Studio for Mac 也可讓您輕鬆地定義新的著色器。 從 [方案總管]  中，以滑鼠右鍵按一下 [資產]  ，然後選取 [新增] > [新增著色器]  。

    ![Visual Studio for Mac 中新的著色器動作](media/unity-image43.png)

7. 著色器檔案格式取得完整的色彩和字型處理，就可以輕鬆地閱讀並了解。

    ![語法醒目提示](media/unity-image44.png)

8. 返回 **Unity**。 您將看到，由於 Visual Studio for Mac 使用相同的專案系統，因此在任一位置所做的變更，將自動與另一個位置同步處理。 現在很容易就能使用最佳工具來完成工作。

    ![Unity 資產面板](media/unity-image45.png)

## <a name="summary"></a>總結

在此實驗室中，您已了解如何開始使用 Unity 與 Visual Studio for Mac 建立遊戲。 若要深入了解 Unity，請參閱 [https://unity3d.com/learn](https://unity3d.com/learn) \(英文\)。
