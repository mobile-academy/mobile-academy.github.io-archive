require 'yaml'
require 'RMagick'

desc 'Runs tests when implementation is changed.'
task :build_miniatures do
  upcoming_dir = "_past"
  d = Dir.new upcoming_dir
  d.each { |file|
    if (file.start_with?('.') == false)
      path = upcoming_dir + '/' + file
      workshop_hash = YAML.load_file(path)
      images = workshop_hash['images']

      image_path = images.first

      puts "Resizing image at path #{image_path}"

      img = Magick::ImageList.new(image_path)

      thumbnail_path = workshop_hash["thumbnail_path"]

      thumbnail = img.resize_to_fit(1024, 768)
      thumbnail.write (thumbnail_path) { self.quality = 80 }

      workshop_hash["thumbnail"]
    end
  }
end
