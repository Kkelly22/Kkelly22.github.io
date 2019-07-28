---
layout: post
title:      "Rails and Prawn"
date:       2019-07-28 17:45:06 -0400
permalink:  rails_and_prawn
---


I'm currently developing an expense upload portal, which in sum, allows a user to upload a receipt and receive an automated email of an expense spreadsheet in return.  There are several major tasks required to make this flow work: uploading a document, extracting the pertinent data from the document, creating a new PDF, and sending this PDF via an automated email.  I'd like to focus on one aspect that was surprisingly simple thanks to a Ruby Gem called "Prawn", and that is PDF generation.  Let's start from the beginning:

1) Go to [Ruby Gems](https://rubygems.org/) and search for [Prawn](https://rubygems.org/gems/prawn).
2) Add the gem to your Gemfile and run bundle install.
3) Identify the point in your application that requires PDF generation, and implement Prawn.  Prawn allows us to generate a PDF with several basic classes at our disposal (i.e. Text, Graphics, Font, and Document).  For example, here is a code snippet of the PDF I am generating which lays down an image first, and then overlays text on top.  Note I am using pixels to act as coordinates:

```
  	def create_pdf(background, path, description)
  		Prawn::Document.generate(path, :page_layout => :portrait) do
  			image background, :image_position => [1,1], :fit => [500,650]
  			draw_text description, :at => [260,450]
  		end
  	end
```

Once I nail down the position and size of my background image, and the position of my text in pixels, I am ready to implement this method by simply calling create_pdf and passing in the arguments I need:

```
    	description = "test description upload"
    	background = Rails.root.join('public', 'expense-report-img.png')
			
    	path = Rails.root.join('public', 'expense-report.pdf')
			
    	create_pdf(background, path, description, price, date)
```

Let's clarify several things going on here:

**A)** Where am I getting my background image?  I am storing this image in my 'public' folder, which lives at the root of my application.  
*~ A quick note about Prawn and images: only PNG and JPG can be used.*

**B)** I specify where I'd like this new PDF to live in my "path" variable.  In my case, I would also like this newly generated PDF to live in my 'public' folder.

Once create_pdf is executed, I check the 'public' folder of my application and see a new file labeled "expense-report.pdf".  Hooray!

*Something to keep in mind when using pixels as coordinates:  Prawn specifies the coordinates [0,0] to be the lower left hand corner of the document, NOT the upper left hand corner.*
