source 'git@gitlab.com:aurapos/ios-pod-spec.git'
source 'https://github.com/cocoapods/specs.git'

ios_version = '12.0'

use_frameworks!

inhibit_all_warnings!

def aura_pods
	pod 'SDWebImage'
	pod 'SwiftGen', '~> 6.0.2'
	pod 'SnapKit', '~> 5'
	pod 'AuraCommon'
	pod 'Firebase/Analytics'
  pod 'Firebase/RemoteConfig'
	pod 'Firebase/Crashlytics'
	pod 'Firebase/Messaging'
	pod 'RxSwift', '~> 5'
  pod 'RxCocoa', '~> 5'
  pod 'RxBiBinding'
	pod 'RxGesture', '~> 3'
	pod 'Moya'
	pod 'RxDataSources'
	pod 'MagazineLayout'
	pod 'Moya/RxSwift'
	pod 'SwiftyBeaver'
	pod 'lottie-ios'
	pod 'RealmSwift'
	pod 'libPhoneNumber-iOS', '= 0.9.13'
	pod 'InputMask',    '= 4.2.0'
	pod 'YandexMapsMobile','4.1.0-lite'
end


target 'Delivery' do
 	aura_pods
end

post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|

            config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = ios_version

            # Checking, whether the target's IPHONEOS_DEPLOYMENT_TARGET currently is lower than "ios_version".
            # If so, change it to "ios_version".
            if Gem::Version.new(ios_version) > Gem::Version.new(config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'])
                config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = ios_version
            end

            config.build_settings['ONLY_ACTIVE_ARCH'] = 'YES'
            config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
        end
    end
end
