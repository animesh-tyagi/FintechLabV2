Create database Customer;
Use Customer;
CREATE TABLE CUST_CL (
  CSTCL_ID BIGINT PRIMARY KEY,
  CSTCL_TYP VARCHAR(100),
  CSTCL_TYP_VALUE VARCHAR(100),
  CSTCL_EFCTV_DATE DATE,
  CSTCL_CRUD_VALUE char(1),
  CSTCL_USER_ID VARCHAR(100),
  CSTCL_WS_ID VARCHAR(100),
  CSTCL_PRGM_ID VARCHAR(100),
  CSTCL_HOST_TS TIMESTAMP,
  CSTCL_LOCAL_TS TIMESTAMP,
  CSTCL_ACPT_TS TIMESTAMP,
  CSTCL_ACPT_TS_UTC_OFST TIMESTAMP,
  CSTCL_UUID VARCHAR(100)
);
CREATE TABLE CUST_ID (
  CST_ID BIGINT PRIMARY KEY,
  CUSTID_TYPE VARCHAR(100),
  CUSTID_ITEM VARCHAR(100) UNIQUE,
  CSTID_EFCTV_DATE DATE,
  CSTID_USER_ID VARCHAR(100),
  CSTID_HOST_TS TIMESTAMP,
  CSTID_UUID VARCHAR(100)
);
CREATE TABLE CUST_DETAILS (
  CST_ID BIGINT PRIMARY KEY,
  CSTDET_TYPE VARCHAR(100), 
  CSTDET_DOB DATE,
  CSTDET_STATUS VARCHAR(100),
  CSTDET_CONTACT VARCHAR(100),
  CSTDET_EMAIL VARCHAR(100),
  CSTDET_EFCTV_DATE DATE,
  FOREIGN KEY (CST_ID) REFERENCES CUST_ID(CST_ID)
);
CREATE TABLE CUST_NAME (
  CST_ID BIGINT,
  CSTNAME_CLS_ID BIGINT,
  CSTNAME_VALUE VARCHAR(100),
  CSTNAME_EFCTV_DATE DATE,
  CSTNAME_USER_ID VARCHAR(100),
  CSTNAME_HOST_TS TIMESTAMP,
  CSTNAME_UUID VARCHAR(100),
  PRIMARY KEY (CST_ID, CSTNAME_CLS_ID),
  FOREIGN KEY (CST_ID) REFERENCES CUST_ID(CST_ID),
  FOREIGN KEY (CSTNAME_CLS_ID) REFERENCES CUST_CL(CSTCL_ID)
);
CREATE TABLE CUST_POI (
  CST_ID BIGINT,
  CSTPOI_CLS_ID BIGINT,
  CSTPOI_VALUE VARCHAR(100) UNIQUE,
  CSTPOI_START DATE,
  CSTPOI_END DATE,
  CSTPOI_USER_ID VARCHAR(100),
  CSTPOI_UUID VARCHAR(100),
  PRIMARY KEY (CST_ID, CSTPOI_CLS_ID),
  FOREIGN KEY (CST_ID) REFERENCES CUST_ID(CST_ID),
  FOREIGN KEY (CSTPOI_CLS_ID) REFERENCES CUST_CL(CSTCL_ID)
);
CREATE TABLE CUST_ADDRESS (
  CST_ID BIGINT,
  CSTADD_CLS_ID BIGINT,
  CSTADD_VALUE VARCHAR(100),
  CSTADD_EFCTV_DATE DATE,
  CSTADD_USER_ID VARCHAR(100),
  CSTADD_HOST_TS TIMESTAMP,
  CSTADD_UUID VARCHAR(100),
  PRIMARY KEY (CST_ID, CSTADD_CLS_ID),
  FOREIGN KEY (CST_ID) REFERENCES CUST_ID(CST_ID),
  FOREIGN KEY (CSTADD_CLS_ID) REFERENCES CUST_CL(CSTCL_ID)
);
