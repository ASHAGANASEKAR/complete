# complete
module Mod
 @v_count=0 
 @doc_count=0
 @a_count=0
 @img_count=0
 def Mod.find(f)
   doc_a=[".txt",".doc",".docx",".pptx",".pdf"]
   vid_a=[".FLV",".mp4",".avi",".3gp",".mkv"]
   aud_a=[".mp3",".sng",".omf"]
   img_a=[".jpg",".TIF",".png",".gif"]
   if doc_a.include?File.extname(f)
     @doc_count+=1
  elsif vid_a.include?File.extname(f)
    @v_count+=1
  elsif aud_a.include?File.extname(f)
    @a_count+=1
  elsif img_a.include?File.extname(f)
    @img_count+=1
  end
 end
  def Mod.walk(start)
    Dir.foreach(start) do |x|
    path=File.join(start,x)
    if x=="." or x==".."
      print"=> "
      next
    elsif File.file?(path)
       find(path)
       puts"/"+ path 
    elsif File.directory?(path)
   walk(path)
  end
 puts "document=#{@doc_count}"
 puts "video=#{@v_count}"
 puts "audio=#{@a_count}"
 puts "image=#{@img_count}"
 end
end
 walk("E:/asha")
end
