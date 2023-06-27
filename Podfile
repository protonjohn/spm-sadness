workspace 'spm-sadness'

# ignore all warnings from all pods
inhibit_all_warnings!

target 'FooApp' do
  project 'FooApp/FooApp.xcodeproj'
  platform :ios, '15.0'
  use_frameworks!

  pod 'GSMessages', '~> 1.0'
  pod 'Alamofire', '5.4.4'
end
  

target 'FooFramework' do
  project 'FooFramework/FooFramework.xcodeproj'
  platform :ios, '15.0'
  use_frameworks!

  pod 'SwiftOTP'
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '15.0'
      config.build_settings['ENABLE_BITCODE'] = 'NO'
      
      # Reset deployment targets to use the one we have on the main project
      config.build_settings.delete 'MACOSX_DEPLOYMENT_TARGET'

      # The swift version setting can be removed once we move to lottie 3.4.2 or higher
      if target.name == 'lottie-ios'
          target.build_configurations.each do |config|
              config.build_settings['SWIFT_VERSION'] = '5.0'
          end
      end
    end
  end
  
  # Fix bundle signing problems started with Xcode 14: https://github.com/CocoaPods/CocoaPods/issues/11402
  installer.pods_project.targets.each do |target|
      if target.respond_to?(:product_type) and target.product_type == "com.apple.product-type.bundle"
          target.build_configurations.each do |config|
              config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
          end
      end
  end
  # End of fix
end
