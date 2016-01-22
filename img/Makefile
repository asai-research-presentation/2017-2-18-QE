
convert=$(shell find ./ -name "*.$(1)" | sed -e s/$(1)/$(2)/g)

.PHONY:	clean all

all: $(call convert,svg,png) $(call convert,svg,xbb) $(call convert,png,xbb) .jpgxbb

.jpgxbb: $(call convert,jpg,jpg)
	ebb -x $(call convert,jpg,jpg)

%.xbb: %.png
	ebb -x $<

%.png: %.svg
	inkscape -f $< -e $*.png -d 150
#	convert $< $*.png
#	if you want to use imagemagick, comment out 'inkscape...' and use 'convert...'

clean:
	-rm -f $(call convert,svg,png) $(call convert,svg,xbb) $(call convert,png,xbb) $(call convert,jpg,xbb)
