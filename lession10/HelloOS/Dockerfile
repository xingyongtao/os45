FROM alpine:latest

RUN apk --no-cache add qemu-system-x86_64 qemu-ui-curses

COPY ./hd.img /hello-os.img

CMD ["qemu-system-x86_64", "-curses", "-drive", "file=/hello-os.img,format=raw,index=0,media=disk"]