# 1. addi sp, sp, -16
    Instruction Type: I-type
    Opcode: 0010011 (ADDI)
    Immediate: -16 = 1111111111110000 (12 bits, sign-extended)
    Registers: sp(rd) = 00010, sp(rs1) = 00010
    | imm[11:0]       | rs1   | funct3 | rd    | opcode   |
    | 111111111000    | 00010 | 000    | 00010 | 0010011  |

# 2. sd ra, 8(sp)
    Instruction Type: S-type
    Opcode: 0100011 (SD) 
    Immediate: 8 = 00000001000 (split into imm[11:5] and imm[4:0])
    Registers: ra(rs2) = 00001, sp(rs1) = 00010
    | imm[11:5] | rs2   | rs1   | funct3 | imm[4:0] | opcode   |
    | 0000000   | 00001 | 00010 | 011    | 01000    | 0100011  |

# 3. addi a5, a5, 100
    Instruction Type: I-type
    Opcode: 0010011 (ADDI)
    Immediate: 100 = 000000110010
    Registers: a5(rd) = 01010, a5(rs1) = 01010
    | imm[11:0]       | rs1   | funct3 | rd    | opcode   |
    | 000000110010    | 01010 | 000    | 01010 | 0010011  |

# 4. bnez a5, 10190
    Instruction Type: B-type
    Opcode: 1100011 (BNE)
    Immediate: 10190 (calculated relative offset, split into imm[12|10:5|4:1|11])
    Registers: a5(rs1) = 01010, x0(rs2) = 00000
    | imm[12|10:5] | rs2   | rs1   | funct3 | imm[4:1|11] | opcode   |
    | 0100000      | 00000 | 01010 | 001    | 100110      | 1100011  |

# 5. addi a0, zero, 1
    Instruction Type: I-type
    Opcode: 0010011 (ADDI)
    Immediate: 1 = 000000000001
    Registers: a0(rd) = 00100, zero(rs1) = 00000
    | imm[11:0]       | rs1   | funct3 | rd    | opcode   |
    | 000000000001    | 00000 | 000    | 00100 | 0010011  |

# 6. lui a0, 0x21
    Instruction Type: U-type
    Opcode: 0110111 (LUI)
    Immediate: 0x21 (20-bit upper immediate)
    Registers: a0(rd) = 00100
    | imm[31:12]      | rd    | opcode   |
    | 000000000000001 | 00100 | 0110111  |

# 7. jal ra, 10418
    Instruction Type: J-type
    Opcode: 1101111 (JAL)
    Immediate: 10418 (split into imm[20|10:1|11|19:12])
    Registers: ra(rd) = 00001
    | imm[20|10:1|11|19:12] | rd    | opcode   |
    | 001010000000000        | 00001 | 1101111  |

# 8. ret
    Instruction Type: JALR (special case for return)
    Opcode: 1100111 (JALR)
    Immediate: 0
    Registers: ra(rd) = 00001, ra(rs1) = 00001
    | imm[11:0]       | rs1   | funct3 | rd    | opcode   |
    | 000000000000    | 00001 | 000    | 00001 | 1100111  |

# 9. addi a1, zero, 100:
    Instruction Type: I-type
    Opcode: 0010011 (ADDI)
    Immediate: 100 = 000000110010
    Registers: a1(rd) = 00101, zero(rs1) = 00000
    | imm[11:0]       | rs1   | funct3 | rd    | opcode   |
    | 000000110010    | 00000 | 000    | 00101 | 0010011  |
   
# 10. add a0, a0, a1
    Instruction Type: R-type
    Opcode: 0110011 (ADD)
    Registers: a0(rd) = 00100, a0(rs1) = 00100, a1(rs2) = 00101
    | funct7  | rs2   | rs1   | funct3 | rd    | opcode   |
    | 0000000 | 00101 | 00100 | 000    | 00100 | 0110011  |


    
   
