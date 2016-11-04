namespace :book do
  desc 'prepare build'
  task :prebuild do
    Dir.mkdir 'images' unless Dir.exists? 'images'
    Dir.glob("book/*/images/*").each do |image|
      FileUtils.copy(image, "images/" + File.basename(image))
    end
  end

  desc 'build basic book formats'
  task :build => :prebuild do
    puts "Converting to HTML..."
    `bundle exec asciidoctor QGIS_book.asc -o QGIS_book.html`
    puts " -- HTML output at QGIS_book.html"

    puts "Converting to PDF... (this one takes a while)"
      `bundle exec asciidoctor-pdf QGIS_book.asc -o QGIS_book.pdf`
    puts " -- PDF  output at QGIS_book.pdf"
  end
  
  desc 'build html book formats'
  task :build_html => :prebuild do
    puts "Converting to HTML..."
    `bundle exec asciidoctor QGIS_book.asc -o QGIS_book.html`
    puts " -- HTML output at My_book.html"
  end 
  
  desc 'build html with github stylesheet'
  task :build_html_gitcss => :prebuild do
      puts "Converting to HTML with github stylesheet..."
      `bundle exec asciidoctor QGIS_book.asc -a stylesheet=github.css -a stylesdir=./stylesheets -o QGIS_book_github_style.html`
      puts " -- HTML output at My_book_github_style.html"
  end  
  
end

task :default => "book:build"
