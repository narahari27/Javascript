<Grid container>
                            <Grid item xs>
                                <Table style={styles.tableLeft}>
                                    <TableHead style={styles.tableHead}>
                                        <TableRow>
                                            <TableCell style={styles.tableCellFixed}> 5 min KPI </TableCell>
                                            <TableCell style={styles.tableCellSmall}> Succ </TableCell>
                                            <TableCell style={styles.tableCellSmall}> Att </TableCell>
                                        </TableRow>
                                    </TableHead>
                                    <TableBody>
                                        {getData(data?.filter((_) => _.displaytype === 'kpi'), true, true)}
                                        {isSmf && (
                                            <TableRow key={`KCI`}>
                                                <TableCell style={styles.tableCell}>KCI</TableCell>
                                                <TableCell style={styles.tableCell}></TableCell>
                                                <TableCell style={styles.tableCell}></TableCell>
                                            </TableRow>
                                        )}
                                        {isSmf && (
                                            getKciData(data?.filter(_ => _.displaytype == 'kci'), true, true)
                                        )}
                                    </TableBody>
                                </Table>
                            </Grid>
                            <Grid item xs>
                                <Table style={styles.tableLeft}>
                                    <TableHead style={styles.tableHead}>
                                        <TableRow>
                                            <TableCell style={styles.tableCellFixed}> 5 min KPI </TableCell>
                                            <TableCell style={styles.tableCellSmall}> Succ </TableCell>
                                            <TableCell style={styles.tableCellSmall}> Att </TableCell>
                                        </TableRow>
                                    </TableHead>
                                    <TableBody>
                                        {getData(data?.filter((_) => _.displaytype === 'kpi'), true, false)}
                                        {isSmf && (
                                            <TableRow key={`KCI2`} style={{height: '23px'}}>
                                                <TableCell style={styles.tableCell}>{' '}</TableCell>
                                                <TableCell style={styles.tableCell}></TableCell>
                                                <TableCell style={styles.tableCell}></TableCell>
                                            </TableRow>
                                        )}
                                        {isSmf && (
                                            getKciData(data?.filter(_ => _.displaytype == 'kci'), true, false)
                                        )}
                                    </TableBody>
                                </Table>
                            </Grid>
