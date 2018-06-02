# More documentation about how to customize your build
# can be found here:
# https://docs.fastlane.tools
fastlane_version "2.54.0"

# This value helps us track success metrics for Fastfiles
# we automatically generate. Feel free to remove this line
# once you get things running smoothly!

#Parameters : Project_Name, CFBundleIdentifier, Display_Name, BUILD_NUMBER, CFBundleShortVersionString, Apple_Pass, Apple_Id, Apple_Team_Id, Release_Type, CRASHLYTICS_API_TOKEN, CRASHLYTICS_BUILD_SECRET, CRASHLYTICS_GROUP, CRASHLYTICS_BUILD_SECRET
generated_fastfile_id "99f2816a-d8ef-4277-af27-7fd5b692aaa5"

default_platform :ios

platform :ios do

  before_all do
    clear_derived_data
  end

  lane :beta do |options|

    cocoapods

    update_app_identifier(
    xcodeproj: ENV["Project_Name"] + ".xcodeproj",
    plist_path: ENV["Project_Name"] + "/Info.plist",
    app_identifier: ENV["CFBundleIdentifier"]
    )

    update_info_plist(
    scheme: ENV["Project_Name"],
    plist_path: ENV["Project_Name"] + "/Info.plist",
    xcodeproj: ENV["Project_Name"] + ".xcodeproj",
    display_name: ENV["Display_Name"],
    app_identifier: ENV["CFBundleIdentifier"]
    )

    set_info_plist_value(
    path: ENV["Project_Name"] + "/Info.plist",
    key: "CFBundleVersion",
    value: ENV["BUILD_NUMBER"]
    )

    set_info_plist_value(
    path: ENV["Project_Name"] + "/Info.plist",
    key: "CFBundleShortVersionString",
    value: ENV["CFBundleShortVersionString"]
    )

    set_info_plist_value(
    path: ENV["Project_Name"] + "/Info.plist",
    key: "API_BASE_URL",
    value: ENV["API_BASE_URL_END_POINT"]
    )

    ENV["FASTLANE_PASSWORD"] = ENV["Apple_Pass"]

    cert(
    development: true,
    username: ENV["Apple_Id"],
    team_id: ENV["Apple_Team_Id"],
    force: false
    )

    sigh(
    development: true,
    force: false,
    app_identifier: ENV["CFBundleIdentifier"],
    username: ENV["Apple_Id"],
    output_path: 'Provisioning_Path'
    )

    gym(
    scheme: ENV["Project_Name"],
    configuration: "Release",
    export_method: ENV["Release_Type"]
    )

    crashlytics(
    api_token: ENV["CRASHLYTICS_API_TOKEN"],
    groups: ENV["CRASHLYTICS_GROUP"],
    build_secret: ENV["CRASHLYTICS_BUILD_SECRET"]
    )

  end
end
