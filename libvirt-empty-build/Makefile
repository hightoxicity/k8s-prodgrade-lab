SHELL := /bin/bash

OUTPUT_DIRNAME=output-libvirt-empty
BOX_NAME=libvirt-empty

all: clean build install

build:
	cd "${CURDIR}"; \
	mkdir -p "${CURDIR}/${OUTPUT_DIRNAME}" || true; \
	qemu-img create -f qcow2 "${CURDIR}/${OUTPUT_DIRNAME}/${BOX_NAME}.qcow2" 20G; \
	cd "${CURDIR}/${OUTPUT_DIRNAME}"; \
	../create_box.sh "./${BOX_NAME}.qcow2"; \
        cd "${CURDIR}";
	#VBoxManage createvm --name "${BOX_NAME}" --ostype Ubuntu_64 --basefolder "${CURDIR}/${OUTPUT_DIRNAME}"; \
	#VBoxManage registervm "${CURDIR}/${OUTPUT_DIRNAME}/${BOX_NAME}/${BOX_NAME}.vbox"; \
	#VBoxManage storagectl ${BOX_NAME} --name "LsiLogic" --add scsi --controller LsiLogic; \
	#vagrant package --base ${BOX_NAME} --output ${CURDIR}/${OUTPUT_DIRNAME}/${BOX_NAME}.box;

install:
	cp ${CURDIR}/${OUTPUT_DIRNAME}/${BOX_NAME}.box ${CURDIR}/../machines/

clean:
	cd ${CURDIR}; \
	rm -rf ${CURDIR}/${OUTPUT_DIRNAME} || true;
