# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT license.

include ../config.mk

INCLUDE_DIR=../include
SRC_DIR=../src
IFLAGS = -I $(INCLUDE_DIR)

all: test_fastgrnn_lr test_rnnpool test_quantized_utils test_quantized_fastgrnn test_quantized_rnnpool

FASTGRNN_DIR=fastgrnn
test_fastgrnn_lr: $(FASTGRNN_DIR)/test_fastgrnn_lr.c $(SRC_DIR)/utils.o $(SRC_DIR)/fastgrnn.o $(SRC_DIR)/classifier.o
	$(CC) -o $@ $^ $(IFLAGS) $(CFLAGS) -lm
test_quantized_fastgrnn: $(FASTGRNN_DIR)/test_quantized_fastgrnn.c $(SRC_DIR)/quantized_utils.o $(SRC_DIR)/quantized_fastgrnn.o
	$(CC) -o $@ $^ $(IFLAGS) $(CFLAGS) -lm

RNNPOOL_DIR=rnnpool
test_rnnpool: $(RNNPOOL_DIR)/test_rnnpool.c  $(SRC_DIR)/utils.o $(SRC_DIR)/fastgrnn.o $(SRC_DIR)/rnnpool.o
	$(CC) -o $@ $^ $(IFLAGS) $(CFLAGS) -lm
test_quantized_rnnpool: $(RNNPOOL_DIR)/test_quantized_rnnpool.c $(SRC_DIR)/quantized_utils.o $(SRC_DIR)/quantized_fastgrnn.o $(SRC_DIR)/quantized_rnnpool.o
	$(CC) -o $@ $^ $(IFLAGS) $(CFLAGS) -lm

UTILS_DIR=utils
test_quantized_utils: $(UTILS_DIR)/test_quantized_utils.c $(SRC_DIR)/quantized_utils.o
	$(CC) -o $@ $^ $(IFLAGS) $(CFLAGS) -lm

.PHONY: clean cleanest

clean: 
	rm -f *.o *.gch test_fastgrnn_lr test_rnnpool test_quantized_utils test_quantized_fastgrnn test_quantized_rnnpool

cleanest: clean
	rm *~
