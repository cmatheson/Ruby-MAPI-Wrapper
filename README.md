brightcove-api
==============

Ruby gem for interacting with the Brightcove media API. http://docs.brightcove.com/en/media/

Requirements
============

* HTTParty
* JSON
* FakeWeb (only for testing)

Install
=======

* sudo gem install brightcove-api

Searching
=========

To replicate one of the brightcove search API examples:

> find all videos that have "football" and "Chicago" in the name, short description, or long
> description, and which also have the tag "free", and also have either the tag "color" or the
> tag "technicolor"

    >> brightcove = Brightcove::API.new(...)
    >> response = brightcove.get('search_videos', {
         :any => [ "tag:color", "tag:technicolor" ],
         :all => ["football", "chicago", "tag:free"]
       })


Example
=======

    >> require 'brightcove-api'
    => true
    >> brightcove = Brightcove::API.new('0Z2dtxTdJAxtbZ-d0U7Bhio2V1Rhr5Iafl5FFtDPY8E.')
    => #<Brightcove::API:0x114dbc8 @token="0Z2dtxTdJAxtbZ-d0U7Bhio2V1Rhr5Iafl5FFtDPY8E.", @api_url="http://api.brightcove.com/services/library">
    >> response = brightcove.get('find_all_videos', {:page_size => 3, :video_fields => 'id,name,linkURL,linkText'})
    => {"items"=>[{"name"=>"Documentarian Skydiving", "id"=>496518762, "linkText"=>nil, "linkURL"=>nil}, {"name"=>"Surface Tricks", "id"=>496518763, "linkText"=>nil, "linkURL"=>nil}, {"name"=>"Free Skiing", "id"=>496518765, "linkText"=>nil, "linkURL"=>nil}], "page_number"=>0, "page_size"=>3, "total_count"=>-1}
    >> response = brightcove.get('find_all_videos', {:page_size => 5, :sort_by => 'PLAYS_TOTAL'})
    => {"items"=>[{"longDescription"=>nil, "name"=>"Wild Slopes '06", "lastModifiedDate"=>"1171324523307", "thumbnailURL"=>"http://brightcove.vo.llnwd.net/d2/unsecured/media/270881183/270881183_502534829_94499905676eb7cd04a558da2adcf6a34f437b88.jpg?pubId=270881183", "tags"=>["adventure", "snowboarding"], "playsTrailingWeek"=>35, "shortDescription"=>"A ski and snowboard movie that challenges the hype and dares you to see what freeskiing and snowboarding have become. Documenting the very best of this year's riding and culture.", "playsTotal"=>4458, "adKeys"=>nil, "id"=>496518766, "length"=>51251, "videoStillURL"=>"http://brightcove.vo.llnwd.net/d2/unsecured/media/270881183/270881183_502534838_f80fe64f052328cd3b2e158d7234003a23091845.jpg?pubId=270881183", "publishedDate"=>"1171324434811", "creationDate"=>"1171267200000", "linkText"=>nil, "economics"=>"FREE", "referenceId"=>"title010", "linkURL"=>nil}, {"longDescription"=>nil, "name"=>"Jellyfish", "lastModifiedDate"=>"1245181300374", "thumbnailURL"=>"http://brightcove.vo.llnwd.net/d7/unsecured/media/270881183/270881183_26530711001_jellyFish.jpg?pubId=270881183", "tags"=>["sea", "custom skins"], "playsTrailingWeek"=>46, "shortDescription"=>"Jellyfish", "playsTotal"=>4081, "adKeys"=>nil, "id"=>26512561001, "length"=>28400, "videoStillURL"=>"http://brightcove.vo.llnwd.net/d7/unsecured/media/270881183/270881183_26519430001_vs-270881183-vid26513829001-img0000.jpg?pubId=270881183", "publishedDate"=>"1245172164326", "creationDate"=>"1245172164326", "linkText"=>nil, "economics"=>"AD_SUPPORTED", "referenceId"=>nil, "linkURL"=>nil}, {"longDescription"=>"Long Description", "name"=>"Demo Title 2", "lastModifiedDate"=>"1263581295791", "thumbnailURL"=>"http://brightcove.vo.llnwd.net/d2/unsecured/media/270881183/270881183_275925069_d1f97c7f07f2a3f4de7b38eda3761f16f39d2a99.jpg?pubId=270881183", "tags"=>[], "playsTrailingWeek"=>1, "shortDescription"=>"Short Description", "playsTotal"=>3876, "adKeys"=>nil, "id"=>276024035, "length"=>418742, "videoStillURL"=>"http://brightcove.vo.llnwd.net/d2/unsecured/media/270881183/270881183_275943599_b7e2ca63c0311fa3f0b027304b41d252f12d2d66.jpg?pubId=270881183", "publishedDate"=>"1161296014264", "creationDate"=>"1161241200000", "linkText"=>"Related Link", "economics"=>"FREE", "referenceId"=>nil, "linkURL"=>"http://www.brightcove.com"}, {"longDescription"=>nil, "name"=>"Dolphins", "lastModifiedDate"=>"1263581295790", "thumbnailURL"=>"http://brightcove.vo.llnwd.net/d7/unsecured/media/270881183/270881183_26531197001_dolphins.jpg?pubId=270881183", "tags"=>["sea", "custom skins"], "playsTrailingWeek"=>30, "shortDescription"=>"Dolphins", "playsTotal"=>3870, "adKeys"=>nil, "id"=>26511963001, "length"=>12800, "videoStillURL"=>"http://brightcove.vo.llnwd.net/d7/unsecured/media/270881183/270881183_26519372001_vs-270881183-vid26510372001-img0000.jpg?pubId=270881183", "publishedDate"=>"1245171732987", "creationDate"=>"1245171732987", "linkText"=>nil, "economics"=>"AD_SUPPORTED", "referenceId"=>nil, "linkURL"=>nil}, {"longDescription"=>nil, "name"=>"Welcome to Brightcove 3", "lastModifiedDate"=>"1225134261511", "thumbnailURL"=>"http://brightcove.vo.llnwd.net/d6/unsecured/media/270881183/270881183_1858983740_brightcove3-thumb.jpg?pubId=270881183", "tags"=>[], "playsTrailingWeek"=>0, "shortDescription"=>"Tareef Kawaf, Brightcove's SVP of Engineering, welcomes you to Brightcove 3.", "playsTotal"=>3349, "adKeys"=>nil, "id"=>1858922805, "length"=>53820, "videoStillURL"=>"http://brightcove.vo.llnwd.net/d6/unsecured/media/270881183/270881183_1858994782_vid-StudioDashboards.jpg?pubId=270881183", "publishedDate"=>"1225134261508", "creationDate"=>"1224096089173", "linkText"=>nil, "economics"=>"AD_SUPPORTED", "referenceId"=>nil, "linkURL"=>nil}], "page_number"=>0, "page_size"=>5, "total_count"=>-1}
    >> response = brightcove.post('delete_video', {:video_id => '595153263001'})
    => {}

If you want to perform a file upload, for example, to create a video, you can use the __post_file()__ method.

    >> video_id = brightcove.post_file('create_video', '/path/to/video.mov', :video => {:shortDescription => 'Short Description', :name => 'Video name'})
    => 653155417001

Note on Patches/Pull Requests
=============================

* Fork the project.
* Make your feature addition or bug fix.
* Add tests for it. This is important so I don't break it in a
  future version unintentionally.
* Commit, do not mess with rakefile, version, or history.
  (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
* Send me a pull request. Bonus points for topic branches.

Copyright
=========
Copyright (c) 2010-2011 David Czarnecki. See LICENSE for details.
