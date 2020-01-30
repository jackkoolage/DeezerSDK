## DeezerSDK

`Download:`[https://github.com/jackkoolage/DeezerSDK/releases](https://github.com/jackkoolage/DeezerSDK/releases)<br>
`Help:`[https://github.com/jackkoolage/DeezerSDK/wiki](https://github.com/jackkoolage/DeezerSDK/wiki)<br>
`NuGet:`
[![NuGet](https://img.shields.io/nuget/v/DeQmaTech.DeezerSDK.svg?style=flat-square&logo=nuget)](https://www.nuget.org/packages/DeQmaTech.DeezerSDK)<br>


# Features:
* Assemblies for .NET 4.5.2 and .NET Standard 2.0 and .NET Core 2.1
* Just one external reference (Newtonsoft.Json)
* Easy installation using NuGet
* Upload/Download tracking support
* Proxy Support
* Upload/Download cancellation support


# List of functions:
**Token**
1. GetAccessToken
1. GetVerificationCode
1. ExchangingVerificationCodeForAToken
1. Register

**AccountClient**
1. UserInfo
1. UserOptions
1. ApplicationGrantedPermissions
1. GetCFtoken

**Albums**
1. List
1. ListRecursively
1. Metadata
1. Rate
1. Comments
1. CommentsRecursively

**Artists**
1. ListRecursively
1. List
1. Metadata
1. Albums
1. AlbumsRecursively
1. Comments
1. CommentsRecursively
1. Playlists
1. PlaylistsRecursively
1. Fans
1. FansRecursively
1. Top5Tracks
1. RelatedArtists
1. RelatedArtistsRecursively
1. MixesTracks

**Comments**
1. PlaylistComments
1. PlaylistCommentsRecursively
1. AlbumCommentsRecursively
1. AlbumComments
1. ArtistComments
1. ArtistCommentsRecursively
1. WritePlaylistComment
1. WriteArtistComment
1. WriteAlbumComment
1. Delete
1. Metadata

**Favorites**
1. RemovePlaylist
1. AddPlaylist
1. AddPodcast
1. RemovePodcast
1. AddRadio
1. RemoveRadio
1. AddAlbum
1. RemoveAlbum
1. AddArtist
1. RemoveArtist
1. AddTrack
1. RemoveTrack

**Folders**
1. Metadata
1. List
1. ListRecursively
1. Create
1. AddPlaylist
1. RemovePlaylist
1. AddAlbum
1. RemoveAlbum
1. Items

**Genres**
1. AllGenres
1. Artists
1. Radios
1. Metadata

**History**
1. RecentlyPlayedTracks
1. RecentlyPlayedTracksRecursively

**Mine**
1. RecommendedAlbums
1. RecommendedPlaylists
1. RecommendedArtists
1. RecommendedTracks
1. UploadMP3
1. SetAvatarPicture
1. UnFollow
1. Follow
1. Followers
1. FollowersRecursively
1. Followings
1. FollowingsRecursively
1. IsFollowingMe
1. MyMP3s
1. MyMP3sRecursively
1. ListFlowTracks

**Playlists**
1. List
1. ListRecursively
1. Add
1. AddMultiple
1. Remove
1. RemoveMultiple
1. Metadata
1. Exists
1. Create
1. Edit
1. Delete
1. Clear
1. Rate
1. OrderInPlaylist
1. SetArtwork
1. MarkAsSeen
1. Tracks
1. RecommendationTracks
1. Fans
1. TrackExists
1. Search

**Radios**
1. Tracks
1. List2
1. List3
1. Genres
1. Metadata
1. Top25Radios
1. List
1. ListRecursively

**Search**
1. Playlists
1. Tracks
1. Artists
1. Albums
1. Historys
1. Radios
1. Users
1. AdvancedTracksSearch
1. AutocompleteSearch

**StaffPicks**
1. AlbumsOfTheWeek
1. TopTrackAlbumArtistPlaylist
1. NewAlbumsInCountry
1. NewAlbumsInCountryRecursively

**Tracks**
1. List
1. ListRecursively
1. Delete
1. Metadata
1. Exists
1. GenerateDirectLink

**Users**
1. Metadata
1. Albums
1. AlbumsRecursively
1. Artists
1. ArtistsRecursively
1. Playlists
1. PlaylistsRecursively
1. Followings
1. FollowingsRecursively
1. Followers
1. FollowersRecursively
1. Tracks
1. TracksRecursively
1. Radios
1. RadiosRecursively
1. TopAlbums
1. TopPlaylists
1. TopArtists
1. TopTracks
1. ListFlowTracks
1. PushNotification

# CodeMap:
![codemap](https://i.postimg.cc/3JryFtFg/dz-codemap.png)

# Code simple:
```vb
'first login (one time only)

    Async Sub GetToken()
        Dim scop As New List(Of DeezerSDK.GetToken.ScopesEnum) From {ScopesEnum.delete_library, ScopesEnum.basic_access, ScopesEnum.email, ScopesEnum.listening_history, ScopesEnum.manage_community, ScopesEnum.manage_library, ScopesEnum.offline_access}
        Dim intgrationUrl = DeezerSDK.GetToken.GetAccessToken("app_id", scop)
    End Sub

'Set your client
    Dim Clnt As DeezerSDK.IClient = New DeezerSDK.SClient("xxxxtokenxxxxx", New ConnectionSettings With {.CloseConnection = True, .TimeOut = TimeSpan.FromMinutes(80), .Proxy = New ProxyConfig With {.SetProxy = True, .ProxyIP = "127.0.0.1", .ProxyPort = 80, .ProxyUsername = "user", .ProxyPassword = "123456"}})

'Functions:

        ''Albums
        Await CLNT.Albums("album_id").Comments(50, 0)
        Await CLNT.Albums("album_id").CommentsRecursively()
        Await CLNT.Albums(Nothing).List(50, 0)
        Await CLNT.Albums(Nothing).ListRecursively()
        Await CLNT.Albums("album_id").Metadata()
        Await CLNT.Albums("album_id").Rate(3)

        ''Artists
        Await CLNT.Artists("artist_id").Albums(50, 0)
        Await CLNT.Artists("artist_id").AlbumsRecursively()
        Await CLNT.Artists("artist_id").Comments(50, 0)
        Await CLNT.Artists("artist_id").CommentsRecursively()
        Await CLNT.Artists("artist_id").Fans(50, 0)
        Await CLNT.Artists("artist_id").FansRecursively()
        Await CLNT.Artists(Nothing).List(50, 0)
        Await CLNT.Artists(Nothing).ListRecursively()
        Await CLNT.Artists("artist_id").Metadata()
        Await CLNT.Artists("artist_id").MixesTracks(50)
        Await CLNT.Artists("artist_id").Playlists(50, 0)
        Await CLNT.Artists("artist_id").PlaylistsRecursively()
        Await CLNT.Artists("artist_id").RelatedArtists(50, 0)
        Await CLNT.Artists("artist_id").RelatedArtistsRecursively()
        Await CLNT.Artists("artist_id").Top5Tracks()

        ''Comments
        Await CLNT.Comments(Nothing).AlbumComments("album_id", 50, 0)
        Await CLNT.Comments(Nothing).AlbumCommentsRecursively("album_id")
        Await CLNT.Comments(Nothing).ArtistComments("artist_id", 50, 0)
        Await CLNT.Comments(Nothing).ArtistCommentsRecursively("album_id")
        Await CLNT.Comments("comment_id").Delete
        Await CLNT.Comments("comment_id").Metadata
        Await CLNT.Comments(Nothing).PlaylistComments("playlist_id", 50, 0)
        Await CLNT.Comments(Nothing).PlaylistCommentsRecursively("playlist_id")
        Await CLNT.Comments(Nothing).WriteAlbumComment("album_id", "nice album")
        Await CLNT.Comments(Nothing).WriteArtistComment("artist_id", "nice artist")
        Await CLNT.Comments(Nothing).WritePlaylistComment("playlist_id", "nice playlist")

        ''Genres
        Await CLNT.Genres(Nothing).AllGenres()
        Await CLNT.Genres("genre_id").Artists()
        Await CLNT.Genres("genre_id").Metadata()
        Await CLNT.Genres("genre_id").Radios()

        ''Historys
        Await CLNT.Historys.RecentlyPlayedTracks(OrderByEnum.ARTIST_ASC, 50, 0)
        Await CLNT.Historys.RecentlyPlayedTracksRecursively(OrderByEnum.ARTIST_ASC)

        ''Mine.Account
        Await CLNT.Mine.Account.UserInfo
        Await CLNT.Mine.Account.ApplicationGrantedPermissions
        Await CLNT.Mine.Account.UserOptions

        ''Mine.Favorites
        Await CLNT.Mine.Favorites.AddAlbum("album_id")
        Await CLNT.Mine.Favorites.AddArtist("artist_id")
        Await CLNT.Mine.Favorites.AddPlaylist("playlist_id")
        Await CLNT.Mine.Favorites.AddPodcast("prodcast_id")
        Await CLNT.Mine.Favorites.AddRadio("radio_id")
        Await CLNT.Mine.Favorites.AddTrack("track_id")
        Await CLNT.Mine.Favorites.RemoveAlbum("album_id")
        Await CLNT.Mine.Favorites.RemoveArtist("artist_id")
        Await CLNT.Mine.Favorites.RemovePlaylist("playlist_id")
        Await CLNT.Mine.Favorites.RemovePodcast("prodcast_id")
        Await CLNT.Mine.Favorites.RemoveRadio("radio_id")
        Await CLNT.Mine.Favorites.RemoveTrack("track_id")

        ''Mine.Folders
        Await CLNT.Mine.Folders("folder_id").AddAlbum("album_id")
        Await CLNT.Mine.Folders("folder_id").AddPlaylist("playlist_id")
        Await CLNT.Mine.Folders(Nothing).Create("folderName", True, False, "all my")
        Await CLNT.Mine.Folders("folder_id").Items(50, 0)
        Await CLNT.Mine.Folders(Nothing).List(50, 0)
        Await CLNT.Mine.Folders(Nothing).ListRecursively()
        Await CLNT.Mine.Folders("folder_id").Metadata
        Await CLNT.Mine.Folders("folder_id").RemoveAlbum("album_id")
        Await CLNT.Mine.Folders("folder_id").RemovePlaylist("playlist_id")

        ''Mine
        Await CLNT.Mine.Follow("user_id")
        Await CLNT.Mine.UnFollow("user_id")
        Await CLNT.Mine.Followers(50, 0)
        Await CLNT.Mine.FollowersRecursively()
        Await CLNT.Mine.Followings(50, 0)
        Await CLNT.Mine.FollowingsRecursively()
        Await CLNT.Mine.IsFollowingMe("user_id")
        Await CLNT.Mine.MyMP3s(50, 0)
        Await CLNT.Mine.MyMP3sRecursively()
        Await CLNT.Mine.RecommendedAlbums()
        Await CLNT.Mine.RecommendedArtists()
        Await CLNT.Mine.RecommendedPlaylists()
        Await CLNT.Mine.RecommendedTracks()
        Await CLNT.Mine.ListFlowTracks
        Dim UploadCancellationToken As New Threading.CancellationTokenSource()
        Dim _ReportCls As New Progress(Of DeezerSDK.ReportStatus)(Sub(r)
                                                                      Button41.Text = String.Format("{0}/{1}", (r.BytesTransferred), (r.TotalBytes))
                                                                      Button41.Text = CInt(r.ProgressPercentage)
                                                                      Button41.Text = If(CStr(r.TextStatus) Is Nothing, "Uploading...", CStr(r.TextStatus))
                                                                  End Sub)
        Await CLNT.Mine.SetAvatarPicture("C:\\myimg.jpg", UploadTypes.FilePath, "myimg.jpg", _ReportCls, UploadCancellationToken.Token)
        Await CLNT.Mine.UploadMP3("C:\\myaudio.mp3", UploadTypes.FilePath, "myaudio.mp3", "testing audio", _ReportCls, UploadCancellationToken.Token)

        ''Playlists
        Await CLNT.Playlists("playlist_id").Add("track_id")
        Await CLNT.Playlists("playlist_id").AddMultiple(New List(Of Long) From {{"track_id"}, {"track_id"}})
        Await CLNT.Playlists("playlist_id").Clear
        Await CLNT.Playlists("playlist_id").Create("my tracks list", True, False, Nothing)
        Await CLNT.Playlists("playlist_id").Delete
        Await CLNT.Playlists("playlist_id").Edit("my tracks list", True, False, Nothing)
        Await CLNT.Playlists("playlist_id").Exists
        Await CLNT.Playlists("playlist_id").Fans(50)
        Await CLNT.Playlists(Nothing).List(OrderByEnum.ARTIST_ASC, 50, 0)
        Await CLNT.Playlists(Nothing).ListRecursively(OrderByEnum.TRACK_ASC)
        Await CLNT.Playlists("playlist_id").MarkAsSeen
        Await CLNT.Playlists("playlist_id").Metadata
        Await CLNT.Playlists("playlist_id").OrderInPlaylist("track_id")
        Await CLNT.Playlists("playlist_id").Rate(3)
        Await CLNT.Playlists("playlist_id").RecommendationTracks(OrderByEnum.TRACK_ASC, 50, 0)
        Await CLNT.Playlists("playlist_id").Remove("track_id")
        Await CLNT.Playlists("playlist_id").RemoveMultiple(New List(Of Long) From {{"track_id"}, {"track_id"}})
        Await CLNT.Playlists(Nothing).Search("tracks list", OrderByEnum.ARTIST_ASC)
        Await CLNT.Playlists("playlist_id").SetArtwork("C:\\myimg.jpg", UploadTypes.FilePath, "myimg.jpg", _ReportCls, UploadCancellationToken.Token)
        Await CLNT.Playlists("playlist_id").TrackExists("track_id")
        Await CLNT.Playlists("playlist_id").Tracks(OrderByEnum.ARTIST_ASC, 50, 0)

        ''Radios
        Await CLNT.Radios("radio_id").Metadata
        Await CLNT.Radios(Nothing).Genres()
        Await CLNT.Radios(Nothing).List(50, 0)
        Await CLNT.Radios(Nothing).List2()
        Await CLNT.Radios(Nothing).List3(OrderByEnum.ARTIST_ASC, 50, 0)
        Await CLNT.Radios(Nothing).ListRecursively
        Await CLNT.Radios(Nothing).Top25Radios
        Await CLNT.Radios("radio_id").Tracks(50)

        ''Search
        Await CLNT.Search(50, 0).Albums("whats new", AlbumOrderByEnum.RANKING)
        Await CLNT.Search(50, 0).Artists("emi", ArtistOrderByEnum.ARTIST_ASC)
        Await CLNT.Search(50, 0).Historys("hello", OrderByEnum.DURATION_ASC)
        Await CLNT.Search(50, 0).Playlists("tracks list")
        Await CLNT.Search(50, 0).Radios("pop")
        Await CLNT.Search(50, 0).Tracks("money", OrderByEnum.ARTIST_ASC)
        Await CLNT.Search(50, 0).Users("james")
        Await CLNT.Search(50, 0).AdvancedTracksSearch("hello", "adele", Nothing, 40000, 1000, OrderByEnum.RATING_ASC)
        Await CLNT.Search(50, 0).AutocompleteSearch("emine", OrderByEnum.ARTIST_ASC)

        ''StaffPicks
        Await CLNT.StaffPicks.AlbumsOfTheWeek
        Await CLNT.StaffPicks.NewAlbumsInCountry(50, 0)
        Await CLNT.StaffPicks.NewAlbumsInCountryRecursively()
        Await CLNT.StaffPicks.TopTrackAlbumArtistPlaylist(50)

        ''Tracks
        Await CLNT.Tracks("track_id").Delete
        Await CLNT.Tracks("track_id").Exists
        Await CLNT.Tracks(Nothing).List
        Await CLNT.Tracks(Nothing).ListRecursively
        Await CLNT.Tracks("track_id").Metadata
        CLNT.Tracks(Nothing).GenerateDirectLink("7e4b6942c6c3835dd8c4c1e0988dbd79", "658765292", "3", "1")

        ''Users
        Await CLNT.Users("user_id").Metadata
        Await CLNT.Users("user_id").Albums(50, 0)
        Await CLNT.Users("user_id").AlbumsRecursively
        Await CLNT.Users("user_id").Artists(50, 0)
        Await CLNT.Users("user_id").ArtistsRecursively
        Await CLNT.Users("user_id").Followers(50, 0)
        Await CLNT.Users("user_id").FollowersRecursively
        Await CLNT.Users("user_id").Followings(50, 0)
        Await CLNT.Users("user_id").FollowingsRecursively
        Await CLNT.Users("user_id").ListFlowTracks
        Await CLNT.Users("user_id").Playlists(OrderByEnum.ARTIST_ASC, 50, 0)
        Await CLNT.Users("user_id").PlaylistsRecursively(OrderByEnum.RANKING)
        Await CLNT.Users("user_id").PushNotification("hi there")
        Await CLNT.Users("user_id").Radios(50, 0)
        Await CLNT.Users("user_id").RadiosRecursively
        Await CLNT.Users("user_id").TopAlbums
        Await CLNT.Users("user_id").TopArtists
        Await CLNT.Users("user_id").TopPlaylists
        Await CLNT.Users("user_id").TopTracks
        Await CLNT.Users("user_id").Tracks(OrderByEnum.ARTIST_ASC, 50, 0)
        Await CLNT.Users("user_id").TracksRecursively(OrderByEnum.ALBUM_ASC)
```
