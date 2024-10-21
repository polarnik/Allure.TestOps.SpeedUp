# Indexes

```sql
CREATE INDEX fix_test_result_1282503_new_history_key_idx ON public.test_result USING btree (launch_id, history_key) WHERE (launch_id >= 1282503);

CREATE INDEX fix_test_result_launch_id_inc_id_new_1282503_status1_idx ON public.test_result USING btree (launch_id) INCLUDE (id) WHERE ((launch_id >= 1282503) AND (status = 1));

CREATE INDEX fix_test_result_launch_id_new_1282503_status_idx ON public.test_result USING btree (launch_id, status) WHERE (launch_id >= 1282503);

CREATE INDEX fix_test_result_testcsid_launchid_nonhid_nonmute_new_1282503 ON public.test_result USING btree (launch_id, test_case_id) WHERE ((launch_id >= 1282503) AND ((hidden = false) AND (muted = false)));

CREATE INDEX fix_testresult_launchid_sts_inc_createddate_vis_new_1282503 ON public.test_result USING btree (launch_id, status) INCLUDE (created_date) WHERE ((launch_id >= 1282503) AND ((status = ANY (ARRAY[0, 1, 2, 3])) AND (hidden = false)));

CREATE UNIQUE INDEX fix_udx_test_result_new_id_667139268 ON public.test_result USING btree (id) WHERE (id >= 667139268);

CREATE UNIQUE INDEX fix_udx_custom_field_value_id_minus2_include_name ON public.custom_field_value USING btree (id) INCLUDE (name) WHERE (custom_field_id = '-2'::integer);

CREATE UNIQUE INDEX fix_udx_custom_field_value_id_minus3_include_name ON public.custom_field_value USING btree (id) INCLUDE (name) WHERE (custom_field_id = '-3'::integer);

CREATE UNIQUE INDEX fix_udx_custom_field_value_id_minus5_include_name ON public.custom_field_value USING btree (id) INCLUDE (name) WHERE (custom_field_id = '-5'::integer);

CREATE UNIQUE INDEX fix_udx_custom_field_value_id_plus2_include_name ON public.custom_field_value USING btree (id) INCLUDE (name) WHERE (custom_field_id = 2);

CREATE INDEX fix_launch_id_13_closed ON public.launch USING btree (id) WHERE ((closed = true) AND (project_id = 13));

CREATE INDEX fix_launch_id_28_closed ON public.launch USING btree (id) WHERE ((closed = true) AND (project_id = 28));

CREATE INDEX fix_launch_id_3_closed ON public.launch USING btree (id) WHERE ((closed = true) AND (project_id = 3));

CREATE INDEX fix_launch_last_modified_date_id_13_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 13));

CREATE INDEX fix_launch_last_modified_date_id_15_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 15));

CREATE INDEX fix_launch_last_modified_date_id_25_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 25));

CREATE INDEX fix_launch_last_modified_date_id_28_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 28));

CREATE INDEX fix_launch_last_modified_date_id_30_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 30));

CREATE INDEX fix_launch_last_modified_date_id_34_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 34));

CREATE INDEX fix_launch_last_modified_date_id_3_not_closed ON public.launch USING btree (last_modified_date, id) WHERE ((closed = false) AND (project_id = 3));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_13_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 13));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_15_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 15));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_25_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 25));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_28_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 28));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_30_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 30));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_34_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 34));

CREATE INDEX fix_launch_last_modified_date_id_autoclose_3_not_closed ON public.launch USING btree (id, last_modified_date, autoclose) WHERE ((closed = false) AND (project_id = 3));

CREATE UNIQUE INDEX fix_udx_launch_13_created_date_id ON public.launch USING btree (created_date DESC, id) WHERE (project_id = 13);

CREATE UNIQUE INDEX fix_udx_launch_15_created_date_id ON public.launch USING btree (created_date DESC, id) WHERE (project_id = 15);

CREATE UNIQUE INDEX fix_udx_launch_25_created_date_id ON public.launch USING btree (created_date DESC, id) WHERE (project_id = 25);

CREATE UNIQUE INDEX fix_udx_launch_28_created_date_id ON public.launch USING btree (created_date DESC, id) WHERE (project_id = 28);

CREATE UNIQUE INDEX fix_udx_launch_3_created_date_id ON public.launch USING btree (created_date DESC, id) WHERE (project_id = 3);

CREATE UNIQUE INDEX fix_udx_launch_id_13_inc_name ON public.launch USING btree (id) INCLUDE (name) WHERE (project_id = 13);

CREATE UNIQUE INDEX fix_udx_launch_id_15_inc_name ON public.launch USING btree (id) INCLUDE (name) WHERE (project_id = 15);

CREATE UNIQUE INDEX fix_udx_launch_id_25_inc_name ON public.launch USING btree (id) INCLUDE (name) WHERE (project_id = 25);

CREATE UNIQUE INDEX fix_udx_launch_id_28_inc_name ON public.launch USING btree (id) INCLUDE (name) WHERE (project_id = 28);

CREATE UNIQUE INDEX fix_udx_launch_id_3_inc_name ON public.launch USING btree (id) INCLUDE (name) WHERE (project_id = 3);

CREATE UNIQUE INDEX fix_udx_launch_id_project_id_inc_name ON public.launch USING btree (project_id, id) INCLUDE (name);

CREATE UNIQUE INDEX fix_udx_launch_new_id_1282503 ON public.launch USING btree (id) WHERE (id >= 1282503);

CREATE UNIQUE INDEX fix_udx_launch_projectid_lastdate_autoclose_id ON public.launch USING btree (project_id, last_modified_date DESC, autoclose, id) WHERE (closed = false);

CREATE UNIQUE INDEX fix_udx_launch_projectid_lastdate_id_filter_notclosed_autoclose ON public.launch USING btree (project_id, last_modified_date DESC, id) WHERE ((closed = false) AND (autoclose = true));

CREATE INDEX fix_idx_launch_launch_tag_launch_id_tag_id_11_webkit ON public.launch_launch_tag USING btree (launch_id) WHERE (launch_tag_id = 11);

CREATE INDEX fix_idx_launch_launch_tag_launch_id_tag_id_12_chromium ON public.launch_launch_tag USING btree (launch_id) WHERE (launch_tag_id = 12);

CREATE INDEX fix_idx_launch_launch_tag_launch_id_tag_id_20_a11y ON public.launch_launch_tag USING btree (launch_id) WHERE (launch_tag_id = 20);

CREATE INDEX fix_idx_launch_launch_tag_launch_id_tag_id_35_firefox ON public.launch_launch_tag USING btree (launch_id) WHERE (launch_tag_id = 35);

CREATE INDEX fix_idx_job_run_launchid_stage ON public.job_run USING btree (launch_id, stage);
```

# Automation

```sql
CREATE OR REPLACE PROCEDURE test_2024_09_19()
LANGUAGE plpgsql
AS $$
DECLARE
    m_test_result_id bigint;
	m_launch_id bigint;
	sql_stmt CHARACTER VARYING(1024);
	old_idx_name_record RECORD;
BEGIN
	CREATE TEMP TABLE temptableforidx AS
	SELECT indexrelname as oldidxname
	from pg_catalog.pg_stat_all_indexes l
	where indexrelname like 'fix%' and indexrelname like '%new%';

	SELECT max(id) INTO m_launch_id from "launch" ;
	SELECT max(id) INTO m_test_result_id from "test_result" tr;

	--create new indexes

	--1- fix_test_result_{LAUNCH_ID}_new_history_key_idx
	sql_stmt := FORMAT(
			'CREATE INDEX concurrently fix_test_result_%s_new_history_key_idx
			ON public.test_result USING btree (launch_id, history_key)
			WHERE (launch_id >= %s);',
		m_launch_id,
        m_launch_id
	);
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);


	---
	--2- fix_udx_test_result_new_id_{TEST_RESULT_ID}
	sql_stmt := FORMAT(
			'CREATE UNIQUE INDEX concurrently fix_udx_test_result_new_id_%s
			ON public.test_result USING btree (id)
			WHERE (id >= %s);',
		m_test_result_id,
        m_test_result_id
	);
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);


	---
	--3- fix_test_result_launch_id_new_{LAUNCH_ID}_status_idx
	sql_stmt := FORMAT(
			'CREATE INDEX concurrently fix_test_result_launch_id_new_%s_status_idx
			ON public.test_result USING btree (launch_id, status)
			WHERE (launch_id >= %s);',
		m_launch_id,
        m_launch_id
	);
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);


	---
	--4- fix_test_result_launch_id_inc_id_new_{LAUNCH_ID}_status1_idx
	sql_stmt := FORMAT(
			'CREATE INDEX concurrently fix_test_result_launch_id_inc_id_new_%s_status1_idx
			ON public.test_result USING btree (launch_id) INCLUDE (id)
			WHERE ((launch_id >= %s)
			AND (status = 1));',
		m_launch_id,
        m_launch_id)
	;
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);


	---
	--5- fix_test_result_testcaseid_launchid_nonhidden_nonmute_new_{LAUNCH_ID}
	sql_stmt := FORMAT(
			'CREATE INDEX concurrently fix_test_result_testcaseid_launchid_nonhidden_nonmute_new_%s
			ON public.test_result USING btree (launch_id, test_case_id)
			WHERE ((launch_id >= %s)
			AND ((hidden = false)
			AND (muted = false)));',
		m_launch_id,
        m_launch_id)
	;
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);

	---
	--6- fix_testresult_launchid_status_inc_createddate_vis_new_{LAUNCH_ID}
	sql_stmt := FORMAT(
			'CREATE INDEX concurrently fix_test_result_testcaseid_launchid_nonhidden_nonmute_new_%s
			ON public.test_result USING btree (launch_id, status) INCLUDE (created_date)
			WHERE ((launch_id >= %s)
			AND ((status = ANY (ARRAY[0, 1, 2, 3]))
			AND (hidden = false)));',
		m_launch_id,
        m_launch_id)
	;
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);

	---
	--7- fix_udx_launch_new_id_{LAUNCH_ID}
	sql_stmt := FORMAT(
			'CREATE UNIQUE INDEX concurrently fix_udx_launch_new_id_%s
			ON public.launch USING btree (id)
			WHERE (id >= %s);',
		m_launch_id,
        m_launch_id)
	;
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);

	--
	--8- fix_udx_launch_new_id_{LAUNCH_ID}
	sql_stmt := FORMAT(
			'CREATE UNIQUE INDEX concurrently fix_test_session_id_launch_id_new_%s
			ON public.test_session USING btree (id, launch_id)
			WHERE (launch_id >= %s);',
		m_launch_id,
        m_launch_id)
	;
	RAISE NOTICE 'SQL: %', sql_stmt;
	--EXECUTE(sql_stmt);


	FOR old_idx_name_record in SELECT oldidxname from temptableforidx
	LOOP
		sql_stmt := FORMAT(
			'DROP INDEX IF EXISTS %s;',
			old_idx_name_record.oldidxname
		);
		--EXECUTE(sql_stmt);
		RAISE NOTICE 'To Delete: %', sql_stmt;
	END LOOP;

	--drop temp table
	DROP TABLE temptableforidx;

END;
$$;
```