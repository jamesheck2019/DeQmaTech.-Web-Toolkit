## ProxySDK

`Download:`[https://github.com/jamesheck2019/ProxySDK/releases](https://github.com/jamesheck2019/ProxySDK/releases)<br>
`NuGet:`
[![NuGet](https://img.shields.io/nuget/v/DeQmaTech.ProxySDK.svg?style=flat-square&logo=nuget)](https://www.nuget.org/packages/DeQmaTech.ProxySDK)<br>

**Features**
* Assemblies for .NET 4.5.2 and .NET Standard 2.0 and .NET Core 2.1
* Just one external reference (Newtonsoft.Json)
* Easy installation using NuGet
* Proxy Support

# Supported Providers:
* gimmeproxy.com
* ip2proxy.com
* pubproxy.com
* getproxylist.com
* proxy-list.download
* proxycheck.io

# Code simple:
```vb.net
    Sub SetClient()
        Dim MyClient As ProxySDK.IProxy = New ProxySDK.ProxyClient()
    End Sub
```
```vb.net
    Sub SetClientWithOptions()
        Dim Optians As New ProxySDK.ConnectionSettings With {.CloseConnection = True, .TimeOut = TimeSpan.FromMinutes(30), .Proxy = New ProxySDK.ProxyConfig With {.ProxyIP = "172.0.0.0", .ProxyPort = 80, .ProxyUsername = "myname", .ProxyPassword = "myPass", .SetProxy = True}}
        Dim MyClient As ProxySDK.IProxy = New ProxySDK.ProxyClient(Optians)
    End Sub
```
```vb.net
    Async Sub GetProxyFromGimme()
        Dim result = Await MyClient.Gimme()
        DataGridView1.Rows.Add(result.ip, result.ipPort, result.country)
    End Sub
```
```vb.net
    Async Sub GetProxyFromPubproxy()
        Dim result = Await MyClient.Pubproxy()
        For Each vid In result.data
            DataGridView1.Rows.Add(vid.ip, vid.ipPort, vid.country, vid.speed)
        Next
    End Sub
```
```vb.net
    Async Sub GetProxyFromGetproxylist()
        Dim result = Await MyClient.Getproxylist()
        DataGridView1.Rows.Add(result.ip, result.port, result.country, result.uptime)
    End Sub
```
```vb.net
    Async Sub GetProxyFromProxylistdownload()
        Dim result = Await MyClient.Proxylistdownload(ProxyTypeEnum.https, AnonTypeEnum.anonymous, ProxyCountryEnum.US)
        For Each vid In result
            DataGridView1.Rows.Add(vid.ip, vid.port, vid.IP_AND_PORT)
        Next
    End Sub
```
```vb.net
    Async Sub CheckProxy()
        Dim result = Await MyClient.CheckProxyStatus("172.1.0.0", 80)
        DataGridView1.Rows.Add(result.proxy, result.provider, result.type, result.city, result.country)
    End Sub
```
