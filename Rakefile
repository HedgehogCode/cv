# coding: utf-8
abort('Please run this using `bundle exec rake`') unless ENV["BUNDLE_BIN_PATH"]
require 'pdfkit'

desc 'Build the CV'
task :build => [:build_webpage, :build_pdf]

desc 'Build the webpage'
task :build_webpage do
  sh 'bundle exec jekyll build --source ./cv'
end

desc 'Preview the webpage'
task :preview do
  sh 'bundle exec jekyll serve --source ./cv --watch --drafts'
end

desc "Build the PDF"
task :build_pdf => [:build_webpage] do
  begin
    options = {
      :page_size => 'A4',
      :print_media_type => true,
      :quiet => false
    }
    kit = PDFKit.new(File.new('./_site/index.html'), options)
    file = kit.to_file('./_site/cv_benjamin_wilhelm.pdf')
  rescue => msg
    puts "#{msg}"
  end
end

task :default => [:build]
