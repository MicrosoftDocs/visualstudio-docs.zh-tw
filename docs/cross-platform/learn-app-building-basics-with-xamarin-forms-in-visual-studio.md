---
title: 了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: f9f233b5f43555f86f0a49c5e5853cad6d7456b1
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924420"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念

在您完成[設定和安裝](../cross-platform/setup-and-install.md)及[驗證您的 Xamarin 環境](../cross-platform/verify-your-xamarin-environment.md)中的步驟之後，本逐步解說會示範如何使用 Xamarin.Forms 來建置基本的應用程式。 使用 Xamarin.Forms 時，您將只在 .NET Standard 類別庫中撰寫所有的 UI 程式碼一次。 接著，Xamarin 將會針對 iOS、Android 和通用 Windows 平台自動呈現原生 UI 控制項。

通常就此通用程式碼而言，使用 .NET Standard 程式庫會比使用共用專案好。 .NET Standard 程式庫包含可在所有目標平台上執行的 .NET API。

以下是您將建置的應用程式。 它會在 iOS 和 Android 手機及 Windows 10 的「通用 Windows 平台」(UWP) 上執行 (從左到右)：

[![iOS、Android 及 UWP 上的天氣應用程式範例](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

您將執行下列步驟來建置此應用程式：

-   [設立方案](#solution)

-   [寫入共用的資料服務程式碼](#dataservice)

-   [開始寫入共用的 UI 程式碼](#uicode)

-   [使用 Visual Studio Emulator for Android 測試您的應用程式。](#test)

-   [完成 UI 使其具備跨平台的原生外觀與風格](#finish)

> [!TIP]
> 您可以在 [GitHub 上的 xamarin-forms-samples 存放庫](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)找到本專案的完整原始程式碼。

<a name="solution" />

## <a name="set-up-your-solution"></a>設立方案

下列步驟會建立 Xamarin.Forms 方案，其中包含共用程式碼的 .NET Standard 類別庫，以及兩個新增的 NuGet 套件。

1. 在 Visual Studio 中，建立新的 [跨平台應用程式 (Xamarin.Forms)] 方案，並將其命名為 **WeatherApp**。 從左側清單中選取 [Visual C#] 和 [跨平台] 來尋找範本。

    ![建立新的跨平台 Xamarin.Forms 應用程式專案](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

    如果找不到該範本，您可能必須安裝 Xamarin 或啟用 Visual Studio 2017 功能。 請參閱[設定和安裝](../cross-platform/setup-and-install.md)。

2.  按一下 [確定] 之後，將會有數個選項可供選取。 選擇 [空白應用程式]和 [.NET Standard]：

    ![建立新的跨平台應用程式專案](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")

3.  按一下 [確定] 來建立方案之後，您將會有一個含有四個專案的方案：

    -   **WeatherApp**：您將寫入跨平台共用之程式碼的 .NET Standard 程式庫，其中包括使用 Xamarin.Forms 的一般商務邏輯和 UI 程式碼。

    -   **WeatherApp.Android**：包含原生 Android 程式碼的專案。

    -   **WeatherApp.iOS**：包含原生 iOS 程式碼的專案。

    -   **WeatherApp.UWP**：包含 Windows 10 UWP 程式碼的專案。

    > [!NOTE]
    >  您可以隨意刪除任何不屬於目標平台的專案。

     在每個原生專案內，您都可以存取對應平台的原生設計工具，並可視需要實作平台特定畫面和功能。

4.  將您方案中的 Xamarin.Forms NuGet 套件升級至最新的穩定版本，如下所示：

    -   選取 [工具] > [NuGet 封裝管理員] > [管理方案的 NuGet 封裝]。

    -   選取 [更新] 索引標籤下方的 [Xamarin.Forms] 套件，並選取要更新方案中的所有專案 。 (請勿選取 Xamarin Android 支援程式庫的更新)。

    -   將 [版本]  欄位更新為可使用的 [最新穩定版]  。

    -   按一下 [安裝] 。

         ![更新 Xamarin.Forms NuGet 封裝](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

    您應該養成每次建立新 Xamarin.Forms 方案都升級 Xamarin.Forms 版本的習慣。 請勿更新任何 Android 支援程式庫。 如有必要，將會在您更新 Xamarin.Forms 版本時更新這些程式庫。

5.  將 **Newtonsoft.Json** NuGet 套件新增至 **WeatherApp** 專案。 此程式庫可用來處理從天氣資料服務擷取的資訊：

    -   在 NuGet 套件管理員 (在步驟 4 後仍保持開啟) 中，選取 [瀏覽] 索引標籤，並搜尋 **Newtonsoft**。

    -   選取 **Newtonsoft.Json**。

    -   勾選 [WeatherApp] 專案，這是唯一一個必須安裝套件的專案。

    -   請確認 [版本]  欄位設為 [最新穩定版]  。

    -   按一下 [安裝] 。

    ![找出並安裝 Newtonsoft.Json NuGet 封裝](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

6.  重複步驟 5 以尋找並安裝 .NET Standard 專案中的 **Microsoft.CSharp** 套件。 必須要有此程式庫，才能使用 .NET Standard 程式庫中的 C# `dynamic` 資料類型。

7.  建置方案，並確認沒有任何建置錯誤。

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>寫入共用的資料服務程式碼

您將在 **WeatherApp** .NET Standard 程式庫專案中撰寫跨所有平台共用的程式碼。 iOS、Android 及 Windows 專案的應用程式套件組建會參考此程式庫。

若要執行此範例，您必須先在 [http://openweathermap.org/appid](http://openweathermap.org/appid) 註冊免費的 API 金鑰。

下列步驟接著會將程式碼新增至 .NET Standard 程式庫，以存取並儲存該天氣服務的資料：

1.  以滑鼠右鍵按一下 **WeatherApp** 專案，然後選取 [新增] > [類別...]。在 [加入新項目]  對話方塊中，將檔案命名為 **Weather.cs**。 您將使用此類別儲存天氣資料服務的資料。

2.  以下列程式碼取代整個 **Weather.cs** 的內容：

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```

3.  將另一個名為 **DataService.cs** 的類別新增至 **WeatherApp** 專案，以使用該類別來處理天氣資料服務的 JSON 資料。

4.  以下列程式碼取代整個 **DataService.cs** 的內容：

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5.  在名為 **Core.cs** 的 **WeatherApp** 專案中新增第三個類別，您將在此處放置共用的商務邏輯。 此程式碼會使用郵遞區號來組成查詢字串、呼叫天氣資料服務，然後填入 `Weather` 類別的執行個體。

6.  以下列程式碼取代 **Core.cs** 的內容：

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR API KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. 以您取得的 API 金鑰取代 *YOUR API KEY HERE*。 仍然需要用引號括住它！

8.  建置 **WeatherApp** 程式庫專案，以確保程式碼正確。

 <a name="uicode" />

## <a name="begin-writing-shared-ui-code"></a>開始寫入共用的 UI 程式碼

Xamarin.Forms 可讓您實作 .NET Standard 程式庫中的共用 UI 程式碼。 在下列步驟中，您將在專案中新增一個含有按鈕的頁面。 此按鈕會以您在上一節中所看到天氣服務傳回的資料更新頁面上的文字：

1.  在 [WeatherApp] 專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]，來新增一個名為 **WeatherPage** 的[內容頁面]。在 [新增項目] 對話方塊中，選取 [內容頁面]。 請勿選取 [內容頁面 (C#)] 或 [內容檢視]。 將其命名為 **WeatherPage.xaml**。

    ![新增 Xamarin.Forms XAML 頁面](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

     Xamarin.Forms 是以 XAML 為基礎，因此這個步驟會建立 **WeatherPage.xaml** 檔案以及巢狀的程式碼後置檔案 **WeatherPage.xaml.cs**。 您可以在 XAML 或程式碼中撰寫使用者介面邏輯。 您需要針對這兩項作業，進行本逐步解說中的一些步驟。

2.  若要在 **WeatherPage** 畫面中新增按鈕，請以下列標記取代 **WeatherPage.xaml** 的內容：

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">
      <Button x:Name="getWeatherBtn"
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />
    </ContentPage>
    ```

     請注意，您必須使用 `x:Name` 屬性來定義按鈕名稱，如此才能從程式碼後置檔案內依名稱參考此按鈕。

3.  若要為按鈕的 `Clicked` 事件新增事件處理常式以更新按鈕文字，請以下列程式碼取代 **WeatherPage.xaml.cs** 的內容。 (您可視需要自行將 "60601" 變更為其他郵遞區號)。

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();

                //Set the default binding to a default object for now
                BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  若要在應用程式啟動時開啟 **WeatherPage** 作為第一個畫面，請以下列程式碼取代 **App.xaml.cs** 中的預設建構函式：

    ```csharp
    public App()
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  建置 **WeatherApp** 專案，以確保程式碼正確。

<a name="test" />

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>使用 Visual Studio Emulator for Android 測試您的應用程式。

您現在可以準備執行應用程式！ 現在，我們先執行 Android 版本以確認應用程式可從氣象服務取得資料。 在稍後新增更多 UI 項目之後，您也會執行 iOS 和 UWP 版本。

1.  以滑鼠右鍵按一下 [WeatherApp.Android] 專案，然後選取 [設定為啟始專案] 以將其設為啟始專案。

2.  在 Visual Studio 工具列中，系統會將 **WeatherApp.Android** 列為目標專案。 選取其中一個 Android 模擬器進行偵錯，並按 **F5**。 建議您使用其中一個會在 Android 版 Visual Studio 模擬器中執行應用程式的 **VisualStudio** 模擬器選項。

    ![選取 Android 模擬器偵錯目標](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > 如果 Visual Studio 指出 Android 專案找不到 Newtonsoft.Json 檔案，請將該 NuGet 套件新增至 Android 專案。

3.  在模擬器中啟動應用程式時，請按一下 [獲知天氣]  按鈕。 您應該會看到按鈕的文字更新為 **Chicago**，這就是從天氣服務所擷取資料的 `Title` 屬性。

     ![點選按鈕之前和之後的氣象應用程式](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

<a name="finish" />

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>完成 UI 使其具備跨平台的原生外觀與風格

Xamarin.Forms 可針對每個平台呈現原生的 UI 控制項，讓您的應用程式自動擁有原生的外觀與風格。 您只要修飾 UI 來包含郵遞區號的輸入欄位和可顯示天氣資料的控制項，即可更清楚地看到此原生外觀與風格。

1.  以下列標記取代 **WeatherPage.xaml** 的內容。 您可從程式碼中參考依上述方式使用 `x:Name` 屬性來命名的項目。 Xamarin.Forms 也提供一些[版面配置選項](/xamarin/xamarin-forms/user-interface/controls/layouts)。 在這裡，WeatherPage 是使用 [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) 和 [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/)。

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>

                <Label Text="Search by Zip Code"
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />

                <Label x:Name="zipCodeLabel" Text="Zip Code:"
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />

                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />

                <Button x:Name="getWeatherBtn" Text="Get Weather"
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>
     ```

     雖然此處未示範，但您可以在 XAML 檔案中使用 `OnPlatform` 標記來選取目前執行應用程式平台專屬的屬性值 (請參閱[基本 XAML 語法](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/))。在程式碼後置檔案中，您可以藉由將 [`Device.RuntimePlatform`](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) 屬性與 [`Device`](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/) 類別中所定義名為 [`Device.iOS`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/)、[`Device.Android`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/) 及 [`Device.UWP`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/) 的常數做比較，來判斷目前執行應用程式的平台。

2.  在 **WeatherPage.xaml.cs** 中，以下列程式碼取代 `GetWeatherBtn_Clicked` 事件處理常式。 此程式碼會確認輸入欄位中有郵遞區號，然後針對該郵遞區號擷取資料。 接著，它會將整個頁面的繫結內容設定成產生的 `Weather` 執行個體。 此程式碼最後會將按鈕文字設定成「再次搜尋」來作為結束。 UI 中的每個標籤都會繫結至 `Weather` 類別的屬性。 當您將畫面的繫結內容設定為 `Weather` 執行個體時，這些標籤會自動更新。

    ```csharp
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            BindingContext = weather;
            getWeatherBtn.Text = "Search Again";
        }
    }
    ```

3.  在所有三個平台上執行此應用程式，方法是在適當的專案上按一下滑鼠右鍵、選取 [設定為啟始專案]，然後在裝置或模擬器上啟動應用程式。 輸入有效的美國五位數郵遞區號，然後按 [Get Weather] \(獲知天氣\) 按鈕，以顯示該地區的天氣資料。 針對 iOS 專案，您必須將 Visual Studio 連線至您網路上的 Mac 電腦。

     [![iOS、Android 及 UWP 上的天氣應用程式範例](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

本專案的完整原始程式碼位於 [GitHub 上的 xamarin-forms-samples 存放庫](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)。
